# Qt Project Coding Guidelines

Guidelines for code to be contributed to the Qt Project. This might eventually replace the [Coding Conventions](https://wiki.qt.io/Coding_Conventions).

## C++ Language

### Check for C++ features

From Qt 5.7 onwards, Qt code can rely on C++ 11 compliant compilers.  Anyhow, some supported compilers still have incomplete support, or feature compiler bugs. If in doubt use ```QtCore/qcompilerdetection.h``` to check whether the compiler fully implements a feature.

### Use range-based for (carefully)

Prefer to use C++ 11's range-based `for` loop over Qt's `foreach`.

Anyhow, be cautious not to unintentionally force a detach when iterating over an implicitly shared Qt container:

    for (const auto x: qtContainer) {}

will cause `qtContainer` to detach if the container is non-const, and shared. To avoid this, you can use `qAsConst` (from Qt 5.7 onwards):

    for (const auto x: qAsConst(qtContainer)) {}

In addition, there's a [compiler bug](https://connect.microsoft.com/VisualStudio/feedback/details/921721) affecting MSVC 2012 and MSVC 2013.

### Use auto sparingly

### Don't use exceptions

### Care about the memory alignment of data members

### Be careful with the questionmark operator

### Use the constructor to cast simple types

### Do not use global variables of types with a constructor

### Avoid 64-bit enum values

### Use static keyword instead of anonymous namespace


## Qt Interfaces

### Use Q_ENUM instead of Q_ENUMS

### Use Q_DECLARE_TYPEINFO for types that might be used in a container

### Always add the Q_OBJECT macro to QObject derived classes

### Do not inherit from template or tool classes

### Do not inline virtual destructors in exported classes


### Always reimplement event() for public QWidget based classes

## Miscellaneous

### Prefer QVector over QList

### Use qobject_cast instead of dynamic_cast

### Use QStringLiteral / QByteArrayLiteral wisely

### Prefer Qt 5 connect style

### Use logging categories

