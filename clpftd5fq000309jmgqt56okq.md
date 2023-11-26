---
title: ".NET 8: Key updates and Features you need to know."
seoTitle: ".NET 8: Key updates and Features you need to know."
seoDescription: "Uncovering the key updates and features of the new .NET 8 and C# 12"
datePublished: Sun Nov 26 2023 18:28:39 GMT+0000 (Coordinated Universal Time)
cuid: clpftd5fq000309jmgqt56okq
slug: net-8-key-updates-and-features-you-need-to-know
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700588426218/f31851bb-dc8d-44f4-b03b-7af4e0f3d2a7.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1701023042659/ba7ce18b-de88-4b4a-9469-895708db035c.png
tags: csharp, microsoft, net, aspnet, aspnet-core, clean-architecture

---

As Microsoft continues to innovate and evolve its renowned framework, .NET 8 and C# 12 bring a plethora of updates and features that are set to redefine how developers approach .NET applications. Whether you're a seasoned .NET veteran or just starting your journey with C#, this release packs something for everyone. From enhanced performance optimizations to new language features and more robust security enhancements, .NET 8 is poised to streamline your development experience and open new horizons in building efficient, modern applications and C# 12 introduces some new functionalities that can optimize your codebase

# First, we look at .NET 8

As Microsoft releases its latest long-term support version of .Net, It comes with a lot of feature sets and as many as there are, I would only talk about my personal top 5, which are:

* .NET Aspire
    
* Improved JSON Serialization
    
* Native AOT support
    
* New .NET SDK (build, workload, publish, pack)
    
* Garbage collection
    

## .NET Aspire

My personal favourite feature, .NET Aspire marks a significant step forward in the realm of cloud-native application development, offering an advanced, opinionated framework tailored for creating distributed applications that are not only production-ready but also excel in observability. This innovative stack, designed specifically for the cloud environment, simplifies the development of robust, scalable applications by encapsulating best practices and patterns essential for today's distributed systems. Delivered through a suite of specialized NuGet packages, each addressing distinct cloud-native concerns, where they consume a large number of services, such as databases, messaging, and caching. .NET Aspire integrates seamlessly with the .NET 8 platform. , it presents developers with a streamlined pathway to harness the full potential of cloud computing, ensuring their applications are both resilient and efficient in a distributed landscape. This integration signifies a leap in facilitating the creation of high-quality, cloud-optimized applications with .NET.

.NET Aspire offers

1. **Orchestration**:
    
    * In the world of distributed systems, orchestrating multiple projects and their dependencies is a complex task. .NET Aspire simplifies this by providing robust orchestration capabilities. It allows developers to efficiently run and interconnect various components of multi-project applications, ensuring smooth communication and operation across different services and microservices.
        
    * This orchestration support is crucial for handling the dynamic nature of cloud environments where applications need to scale, update, and interact seamlessly. It manages the complexities of deployment, scaling, and networking, making it easier for developers to focus on building the core functionalities of their applications.
        
2. **Components**:
    
    * The components of .NET Aspire are delivered as NuGet packages, covering a range of commonly used services in cloud-native development, such as caching with Redis or database interactions with Postgres.
        
    * These components feature standardized interfaces, which means they can be integrated into applications with consistency and minimal friction. This standardization ensures that regardless of the specific service being used, it adheres to a predictable and reliable pattern of interaction, contributing to more maintainable and scalable codebases.
        
    * By abstracting the complexities of these services into easy-to-integrate packages, .NET Aspire significantly reduces the overhead and potential errors associated with manually setting up and configuring these services.
        
3. **Tooling**:
    
    * .NET Aspire enhances the developer experience by providing specialized project templates and tooling within familiar environments like Visual Studio and the dotnet CLI.
        
    * These tools are designed to streamline the process of creating, managing, and interacting with .NET Aspire applications. From scaffolding new projects to integrating various components, the tooling support makes these tasks more intuitive and efficient.
        
    * The integration with Visual Studio and the dotnet CLI ensures that developers can leverage the full power of .NET Aspire without having to leave their preferred development environment, offering a seamless and productive experience.
        

Nick Chapsas. has a more detailed video on .NET Aspire [Here](https://www.youtube.com/watch?v=DORZA_S7f9w&t=98s)

## Improved JSON Serialization

he .NET 8 release brings several key improvements to the `System.Text.Json` serialization and deserialization functionalities, enhancing the flexibility and efficiency of JSON handling in .NET applications. Here's a summary of my top 9 improvements:

1. **Custom Handling of Missing Members**: You can now customize how to handle members that are not present in the JSON payload, improving error handling and data integrity.
    
2. **Support for Additional Types**: The serializer now supports new types such as `Half`, `Int128`, and `UInt128`, along with `Memory<T>` and `ReadOnlyMemory<T>` values, broadening the range of data types you can easily serialize and deserialize.
    
3. **Source Generator Enhancements**: The System.Text.Json source generator has been improved for Native AOT compatibility, including support for required and init properties, better formatting, and new diagnostics.
    
4. **Interface Hierarchies**: Support has been added for serializing properties from interface hierarchies, allowing for more versatile data structure serialization.
    
5. **New Naming Policies**: `JsonNamingPolicy` includes new policies for snake\_case and kebab-case, offering more options for property name conversions.
    
6. **Read-Only Properties**: The serializer now supports deserializing onto read-only fields or properties, a significant enhancement for working with immutable data structures.
    
7. **New JsonNode API Methods**: Several new methods have been added to `JsonNode` and `JsonArray` classes, such as `DeepClone`, `DeepEquals`, and others for enhanced JSON node manipulation.
    
8. **Serialization of Non-Public Members**: You can now include non-public members in the serialization contract using attributes, increasing the flexibility of data models.
    
9. **Freeze a JsonSerializerOptions Instance**: New methods allow you to freeze a `JsonSerializerOptions` instance, ensuring immutability and thread safety.
    

Visit the Microsoft Release notes for more info [Here](https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-8#serialization)

## Native AOT support

Publishing applications using Native AOT (Ahead-of-Time Compilation) in .NET is a significant feature, especially for scenarios where you want a fully self-contained, efficient, and performant executable. Native AOT compiles the .NET code to native code at build time, resulting in an application that doesn't require the .NET runtime to be installed on the target machine. With .NET 8, there have been notable improvements in this area:

### **Key Improvements in .NET 8 for Native AOT Publishing**

1. **Support for Additional Architectures on macOS**:
    
    * .NET 8 adds support for the x64 and Arm64 architectures on macOS. This expansion means that developers can now build Native AOT applications for a broader range of macOS hardware, including the newer Arm64-based Macs, ensuring better performance and compatibility.
        
2. **Significant Reduction in App Sizes on Linux**:
    
    * One of the remarkable improvements in .NET 8 is the reduction of the sizes of Native AOT apps on Linux, by up to 50%. This reduction is particularly important for deployment and distribution, as it makes the applications more lightweight and easier to distribute.
        

### **Implications and Benefits**

* **Enhanced Performance**: Native AOT-compiled applications run more efficiently since they are executed directly by the hardware without the need for JIT (Just-In-Time) compilation at runtime.
    
* **Increased Compatibility**: With support for more architectures, particularly on macOS, applications can reach a wider audience and are assured of running optimally on different hardware configurations.
    
* **Smaller Footprint**: The reduction in app size is particularly beneficial for environments where storage or bandwidth is a constraint. Smaller applications are easier to deploy, update, and distribute, especially in cloud and edge computing scenarios.
    
* **Simplified Deployment**: Since Native AOT apps are fully self-contained and do not require an external runtime, deployment becomes simpler and more predictable. This is an advantage in environments where installing and updating a runtime can be challenging.
    

Visit the Microsoft Release notes for more info [Here](https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-8#native-aot-support)

## New .NET SDK

The SDK has been improved significantly but I would only be talking about the `dotnet build`, `dotnet publish`, `dotnet workload` and `dotnet pack` commands

The `dotnet build` command in .NET has been updated to include a new option that enhances the build output for a more modernized and informative experience. This updated output format offers several key improvements:

1. **Grouped Errors**: Errors are now grouped with the respective projects they originate from, making it easier to identify and address issues in multi-project solutions.
    
2. **Improved Multi-targeting Visibility**: For projects targeting multiple frameworks, the build output more clearly differentiates between the different target frameworks, providing better visibility into the build process for each framework.
    
3. **Real-time Build Information**: The build process now provides real-time information, offering immediate insights into what the build is currently doing, which improves the overall developer experience in monitoring and understanding the build process.
    

These enhancements make the build output more user-friendly, especially for complex projects, and aid in quicker identification and resolution of build-related issues.

.NET 8 introduces a new `workload clean` command designed to help clean up residual workload packs that may accumulate through multiple updates of the .NET SDK or Visual Studio. This command is useful for resolving issues related to workload management by safely restoring to a known, stable state before attempting further workload operations.

In .NET, the `dotnet publish` and `dotnet pack` commands are used for preparing applications and libraries for deployment and distribution. Traditionally, these commands required specifying a configuration (like Debug or Release) to determine the type of build artifacts they produce. With the recent update, these commands have been modified to produce Release assets by default. The Release configuration in .NET is optimized for production. It includes performance optimizations and typically excludes debug information. By defaulting to Release, `dotnet publish` and `dotnet pack` now align more closely with their intended use cases, preparing assets for production.

## Garbage collection

.NET 8 introduces a new feature allowing for dynamic adjustment of memory limits, which is particularly beneficial in cloud-service environments. This feature enables services to scale their resource consumption up or down in response to fluctuating demand. When a service detects a decrease in demand, it can now reduce its memory limit to lower resource usage and be more cost-effective. Previously, adjusting the memory limit was problematic as the garbage collector (GC) might not recognize the change and could allocate more memory than permitted. However, with .NET 8, the `RefreshMemoryLimit()` API can be called to inform the GC of the new memory limit, ensuring it aligns with the current resource needs of the application. This enhancement aids in optimizing resource utilization and cost efficiency in variable-demand scenarios. SO COOL!!!

# Now let's take a look at C# 12

Coupled with .Net 8, I would only talk about my personal top 5 new improvements to C# 12 which are:

* Primary Constructors
    
* Collection Expressions
    
* Default Lambda params
    
* Aliases as any type
    
* Inline arrays
    

## Primary Constructors

In .NET 8, the ability to create primary constructors has been extended beyond record types to include all classes and structs. This enhancement means that you can now define primary constructors directly in the class or struct declaration, offering a more concise and expressive way to initialize objects, irrespective of whether they are records, classes, or structs.

**Here is an example**

Here we have a Record of Employee

```csharp
// USAGE
        // var staff = new PrimaryConstructors.Employee(1, "Bala", "Jr Developer");
        // var promoted = staff.Promote("Sr Developer", 3);
        // Console.WriteLine(promoted);
        /// <summary>
        /// Represents an employee with properties for age, name, position, and years of experience.
        /// </summary>

        public record Employee(int age, string name, string position)
        {
            public int yearsOfExperience { get; init; }

            public Employee(int Age, string Name, string Position, int yox) : this(Age, Name, Position)
            {
                yearsOfExperience = yox;
            }

            public Employee Promote(string newPosition, int additionalYears)
            {
                return this with
                {
                    position = newPosition,
                    yearsOfExperience = additionalYears + additionalYears
                };
            }
        }
    }
```

With Primary Constructors

```csharp
// USAGE
        // var staff = new PrimaryConstructors.Employee(1, "Bala", "Jr Developer");
        // var promoted = staff.Promote("Sr Developer", 3);
        // Console.WriteLine(promoted);
        /// <summary>
        /// Represents an employee with properties for age, name, position, and years of experience.
        /// </summary>

       public class Employee(int age, string name, string position)
        {
          public int YearsOfExperience { get; init; }

          public Employee(int age, string name, string position, int yearsOfExperience)
           : this(age, name, position)
           {
             YearsOfExperience = yearsOfExperience;
           }

          public Employee Promote(string newPosition, int additionalYears)
          {
            return new Employee(age, name, newPosition, YearsOfExperience + additionalYears);
          }
        }
```

It's fairly the same but used to promote clean code.

## Collection Expressions

In other programming languages like TypeScript, the spread operator (`...`) allows an iterable such as an array or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where key-value pairs are expected. Simply put a spread operator copies items in an iterable into another iterable.

FINALLY, C# 12 has its spread operator. Better late than never right

but rather than that of TypeScript, `(...)` it is `(..)` .

Here is an example of its usage

```csharp
char[] first_name = ['B','a', 'l','a'];
char[] last_name = ['A', 'b', 'd','u','l','k','a','d','i','t'];
int[] full_name = [..first_name, ..last_name];
foreach (var element in full_name)
{
    Console.Write($"{element}, ");
}
// output:
// B,a,l,a,A,b,d,u,l,k,a,d,i,r
```

## Default Lambda expressions

In C# 12, a new feature allows you to assign default values to parameters in lambda expressions, similar to how you would in methods or local functions. This addition enhances the flexibility of lambda expressions.

Here is an example of its usage.

```csharp
// Calculating the Energy using the mass energy equivalence formula Emc2
var Energy = (int mass, long c_light = 299792458) => mass * (c_light ** 2);

Console.WriteLine(Energy(5)); // Outputs the energy given the object mass of 5
```

## Using Aliases as Types

In C# 12, the `using` alias directive is a powerful feature that allows you to create aliases for types. This can be used not only for named types (like classes or structs) but also for more complex types like tuples, arrays, pointers, and other types used in unsafe code. This feature can enhance the readability and maintainability of your code, especially when dealing with complex type definitions.

Here is an example of its usage.

```csharp
// Create an alias for a complex tuple type
using ResultTuple = System.Tuple<string, int, System.Collections.Generic.List<string>>;

public class Test
{
    public static void Main()
    {
        // Use the alias instead of the full tuple type
        ResultTuple result = new ResultTuple("Test", 1, new System.Collections.Generic.List<string> { "G","A","B","R","I","E","L"});

        Console.WriteLine($"Item1: {result.Item1}, Item2: {result.Item2}, Item3 Count: {result.Item3.Count}");
        // Outputs "Test", 1, 7
    }
}
```

## Inline Arrays

Inline arrays in C# 12 are a performance optimization technique used by runtime teams and library authors. They allow the creation of fixed-size arrays within a struct type. This is beneficial because it enables the storage of array data directly within the struct's memory layout, rather than as a separate heap-allocated array. This approach reduces the overhead associated with heap allocation and can lead to more cache-friendly code, as the data is stored contiguously in memory. Inline arrays are particularly useful in performance-critical applications where minimizing memory allocation and maximizing data locality are important.

Here is an example of its usage.

```csharp
[System.Runtime.CompilerServices.InlineArray(4)]
public struct Buffer
{
    private int _element0;
}
var memBuffer = new Buffer();
for(int i = 0; i<=3;i++){
memBuffer[i] = i
}
```

# Conclusion

.NET 8 introduces several impactful enhancements aimed at improving performance, development efficiency, and the overall capabilities of the framework. Notable features include expanded support for Native AOT, enabling more efficient and smaller-sized self-contained applications, and the introduction of inline arrays in structs for enhanced memory management. .Net Aspire seems to be a promising cloud-native solution with well-defined orchestration, tooling and components

C# 12 introduces features designed to enhance developer productivity and code clarity. It now allows primary constructors in classes and structs, streamlining object initialization by reducing boilerplate code. Array, span, and other collection initializations are also more concise and expressive. Additionally, lambda expressions have been improved with support for default parameter values, simplifying scenarios involving optional arguments and reducing the need for overloads or null checks. Moreover, the `using alias` directive has been extended to alias any type, expanding its utility beyond named types, thereby offering more flexibility in code structuring and readability.

Beautiful days ahead .NET developers 🔥

<div data-node-type="callout">
<div data-node-type="callout-emoji">⭐</div>
<div data-node-type="callout-text">Please follow my blog post and turn on notifications, I try to post as many blogs on topics relating to AI engineering and Software Engineering.</div>
</div>

Thanks.