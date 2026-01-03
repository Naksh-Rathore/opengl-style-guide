# OpenGL Style Guide

## Naming

* For functions which upload the data from the CPU to GPU, prefer names like `uploadData()`.
* For functions which link the shader program, prefer names like `linkShaderProgram()`
* For functions which compile individual shaders, prefer names like `compileShader()`
* Always namespace classes and functions to the folder they are in, for example `collision/aabb2d.h` would have it's functions in `Collision::` namespace
* For any other function name, use descriptive names
* For member variables, use the `m_` prefix.
* Use `std::` for standard functions when possible, avoid not using the prefix such as `std::abs()` vs `abs()`

## Design

* Keep a class called `Application` or `Game` that can be used in as a central point
* Reserve class inheritance only when it makes code cleaner, favour composition rather than inheritance in most instances
* Use structs rather than classes when OOP features are infavourable or for prototyping when verbosity slows down efficiency
* Use classes rather than structs when OOP features are required and when scalability is necessary
* Always use delta time for movement related code to ensure frame-independent results
* Prefer using flags of a boolean or enumeration type (members of objects) for state management and use assertions to prevent silent errors
* Always design code in a way that checks for invariance with assertions and error handling
* Never expose anything to an object's owner if it is not needed, and when it is needed use constant reference getters and setters
*  Use a MVC-style design pattern but do not strictly adhere to it at all times
* Have OpenGL calls at the lowest level possible

## Project Structure

* Have an `Application` or `Game` class that dicates flow.
* Have a `World` and `Renderer` class which choose what and how to render and actually render it respectively.
* Have a `Renderable` class that has a `Mesh`, `Material` (`Shader` and `Texture`) 
* Have an `Entity` class which contains game logic members and a `Transform` class (model matrix). It should not care about being rendered, the `Scene` object does that

## Basic flow

1. `Game` object initializes and sets up everything
2. `Game` object tells the `Scene` object to pass all rendered objects that frame to the renderer (in a compacted way)
3. `Scene` object iterates over every entity and checks if it should be rendered.
4. Rendered objects get passed (in a compacted format) to the renderer.
5. The renderer renders all objects to the screen.
6. Repeat

## Optimizations

* Avoid set uniforms every frame if you do not have to, set them only once if you can
* Use separate VAOs/VBOs per mesh if geometry is vastly different and share meshes and use model matrices when geometry is mostly the same.
* Use EBOs whenever it is available and will make performance and code better
* Avoid `std::cout` anything per frame anytime other than debugging (but use sparingly, even for debugging) because it is unperformant and overflows terminal with characters
