---
title: Jak vytvořit uživatelem definované výjimky s lokalizovanými zprávami o výjimkách
description: Zjistěte, jak vytvořit uživatelem definované výjimky s lokalizovanými zprávami o výjimkách
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: fa0bbfdbfc9408302eec2edd4e4ee4503d2612c7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243346"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="727d5-103">Jak vytvořit uživatelem definované výjimky s lokalizovanými zprávami o výjimkách</span><span class="sxs-lookup"><span data-stu-id="727d5-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="727d5-104">V tomto článku se dozvíte, jak vytvořit uživatelem definované výjimky, které jsou zděděny ze základní <xref:System.Exception> třídy s lokalizovanými zprávami o výjimkách pomocí satelitních sestavení.</span><span class="sxs-lookup"><span data-stu-id="727d5-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="727d5-105">Vytvořit vlastní výjimky</span><span class="sxs-lookup"><span data-stu-id="727d5-105">Create custom exceptions</span></span>

<span data-ttu-id="727d5-106">Rozhraní .NET obsahuje mnoho různých výjimek, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="727d5-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="727d5-107">V některých případech, kdy žádný z nich nevyhovuje vašim potřebám, však můžete vytvořit vlastní výjimky.</span><span class="sxs-lookup"><span data-stu-id="727d5-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="727d5-108">Předpokládejme, že chcete vytvořit, `StudentNotFoundException` který `StudentName` obsahuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="727d5-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="727d5-109">Chcete-li vytvořit vlastní výjimku, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="727d5-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="727d5-110">Vytvořte serializovatelnou třídu, <xref:System.Exception>která dědí z .</span><span class="sxs-lookup"><span data-stu-id="727d5-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="727d5-111">Název třídy by měl končit "Exception":</span><span class="sxs-lookup"><span data-stu-id="727d5-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. <span data-ttu-id="727d5-112">Přidejte výchozí konstruktory:</span><span class="sxs-lookup"><span data-stu-id="727d5-112">Add the default constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. <span data-ttu-id="727d5-113">Definujte všechny další vlastnosti a konstruktory:</span><span class="sxs-lookup"><span data-stu-id="727d5-113">Define any additional properties and constructors:</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a><span data-ttu-id="727d5-114">Vytvořit lokalizované zprávy o výjimce</span><span class="sxs-lookup"><span data-stu-id="727d5-114">Create localized exception messages</span></span>

<span data-ttu-id="727d5-115">Vytvořili jste vlastní výjimku a můžete ji vyvolat kdekoli s kódem, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="727d5-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="727d5-116">Problém s předchozím řádkem je, že `"The student cannot be found."` je jen konstantní řetězec.</span><span class="sxs-lookup"><span data-stu-id="727d5-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="727d5-117">V lokalizované aplikaci chcete mít různé zprávy v závislosti na jazykové verzi uživatele.</span><span class="sxs-lookup"><span data-stu-id="727d5-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="727d5-118">[Satelitní shromáždění](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) jsou dobrý způsob, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="727d5-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="727d5-119">Satelitní sestavení je .dll, který obsahuje prostředky pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="727d5-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="727d5-120">Když požádáte o konkrétní prostředky za běhu, CLR najde tento prostředek v závislosti na jazykové verzi uživatele.</span><span class="sxs-lookup"><span data-stu-id="727d5-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="727d5-121">Pokud pro tuto jazykovou verzi není nalezeno žádné satelitní sestavení, použijí se prostředky výchozí jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="727d5-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="727d5-122">Chcete-li vytvořit lokalizované zprávy o výjimce:</span><span class="sxs-lookup"><span data-stu-id="727d5-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="727d5-123">Vytvořte novou složku s názvem *Zdroje* pro uložení souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="727d5-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="727d5-124">Přidejte do něj nový soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="727d5-124">Add a new resource file to it.</span></span> <span data-ttu-id="727d5-125">Chcete-li to provést v sadě Visual Studio, klepněte pravým tlačítkem myši na složku v **Průzkumníkovi řešení**a vyberte **příkaz Přidat** > soubor prostředků**nové položky** > **Resources File**.</span><span class="sxs-lookup"><span data-stu-id="727d5-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="727d5-126">Pojmenujte soubor *ExceptionMessages.resx*.</span><span class="sxs-lookup"><span data-stu-id="727d5-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="727d5-127">Toto je výchozí soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="727d5-127">This is the default resources file.</span></span>
1. <span data-ttu-id="727d5-128">Přidejte dvojici název/hodnota pro zprávu o výjimce, například na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="727d5-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![Přidání prostředků do výchozí jazykové verze](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="727d5-130">Přidejte nový soubor prostředků pro francouzštinu.</span><span class="sxs-lookup"><span data-stu-id="727d5-130">Add a new resource file for French.</span></span> <span data-ttu-id="727d5-131">*Pojmenujte jej ExceptionMessages.fr-FR.resx*.</span><span class="sxs-lookup"><span data-stu-id="727d5-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="727d5-132">Přidejte dvojici název/hodnota pro zprávu o výjimce znovu, ale s francouzskou hodnotou:</span><span class="sxs-lookup"><span data-stu-id="727d5-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![Přidání prostředků do jazykové verze fr-FR](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="727d5-134">Po sestavení projektu by výstupní složka sestavení měla obsahovat složku *fr-FR* se souborem *DLL,* což je satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="727d5-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="727d5-135">Vyvolání výjimky s kódem, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="727d5-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="727d5-136">Pokud je `TestProject` název projektu a soubor prostředků *ExceptionMessages.resx* je umístěn ve složce *Zdroje* projektu, `TestProject.Resources.ExceptionMessages`je plně kvalifikovaný název souboru prostředků .</span><span class="sxs-lookup"><span data-stu-id="727d5-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="727d5-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="727d5-137">See also</span></span>

- [<span data-ttu-id="727d5-138">Jak vytvořit uživatelem definované výjimky</span><span class="sxs-lookup"><span data-stu-id="727d5-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="727d5-139">Vytváření satelitních sestavení pro aplikace klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="727d5-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="727d5-140">base (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="727d5-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="727d5-141">this (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="727d5-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
