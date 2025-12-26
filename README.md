# OpenGL Style & Debug Guide

## Styling

## Naming

1. For functions which upload the data from the CPU to GPU, prefer names like `uploadData()`.
2. For functions which link the shader program, prefer names like `linkShaderProgram()`
3. For functions which compile individual shaders, prefer names like `compileShader()`
4. Always namespace classes and functions to the folder they are in, for example `collision/aabb2d.h` would have it's functions in `Collision::` namespace
5. Make all files and folders singular
6. For any other function name, use descriptive names
7. For member variables, use the `m_` prefix.
8. Use `std::` for standard functions when possible, avoid not using the prefix such as `std::abs()` vs `abs()`

## Design

1. Keep a class called `Application` or `Game` that can be used in as a central point
2. Reserve class inheritance only when it makes code cleaner, favour composition rather than inheritance in most instances
3. Use structs rather than classes when OOP features are infavourable or for prototyping when verbosity impedes efficiency
4. Use classes rather than structs when OOP features are required and when scalability is necessary
5. Always use delta time for movement related code to ensure frame-independent results
6. Prefer using flags (members of objects) for state management and use assertions to prevent silent errors
7. Always design code in a way that checks for invariance with assertions and error handling
8. Never expose anything to an object's owner if it is not needed, and when it is needed use constant reference getters and setters

## Optimizations

1. Avoid set uniforms every frame if you do not have to, set them only once if you can
2. Use a VAO and VBO per object if geometry is vastly different, use a mesh and model matrices if geometry is mostly the same
3. Use EBOs whenever it is available and will make performance and code better
4. Avoid `std::cout` anything per frame anytime other than debugging (but use sparingly, even for debugging) because it is unperformant and overflows terminal with characters

## Debugging
