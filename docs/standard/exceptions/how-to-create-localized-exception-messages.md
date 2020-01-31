---
title: Postup vytvoření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek
description: Naučte se vytvářet uživatelsky definované výjimky s lokalizovanými zprávami výjimek.
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 48e429a6379b0a13cb81f8db6fae27aa31409840
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794615"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="5c383-103">Postup vytvoření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek</span><span class="sxs-lookup"><span data-stu-id="5c383-103">How to create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="5c383-104">V tomto článku se naučíte, jak vytvořit uživatelsky definované výjimky, které jsou zděděné ze základní <xref:System.Exception> třídy s lokalizovanými zprávami výjimek pomocí satelitních sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c383-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="5c383-105">Vytváření vlastních výjimek</span><span class="sxs-lookup"><span data-stu-id="5c383-105">Create custom exceptions</span></span>

<span data-ttu-id="5c383-106">Rozhraní .NET obsahuje mnoho různých výjimek, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="5c383-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="5c383-107">Nicméně v některých případech, pokud žádná z nich nevyhovuje vašim potřebám, můžete vytvořit vlastní výjimky.</span><span class="sxs-lookup"><span data-stu-id="5c383-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="5c383-108">Předpokládejme, že chcete vytvořit `StudentNotFoundException`, který obsahuje vlastnost `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="5c383-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="5c383-109">Chcete-li vytvořit vlastní výjimku, použijte následující postup:</span><span class="sxs-lookup"><span data-stu-id="5c383-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="5c383-110">Vytvořte serializovatelný třídu, která dědí z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="5c383-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="5c383-111">Název třídy by měl končit "výjimku":</span><span class="sxs-lookup"><span data-stu-id="5c383-111">The class name should end in "Exception":</span></span>

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

1. <span data-ttu-id="5c383-112">Přidejte výchozí konstruktory:</span><span class="sxs-lookup"><span data-stu-id="5c383-112">Add the default constructors:</span></span>

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

1. <span data-ttu-id="5c383-113">Definujte jakékoli další vlastnosti a konstruktory:</span><span class="sxs-lookup"><span data-stu-id="5c383-113">Define any additional properties and constructors:</span></span>

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

## <a name="create-localized-exception-messages"></a><span data-ttu-id="5c383-114">Vytvoření lokalizovaných zpráv výjimek</span><span class="sxs-lookup"><span data-stu-id="5c383-114">Create localized exception messages</span></span>

<span data-ttu-id="5c383-115">Vytvořili jste vlastní výjimku a můžete ji vyvolat kdekoli pomocí kódu podobného následujícímu:</span><span class="sxs-lookup"><span data-stu-id="5c383-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

<span data-ttu-id="5c383-116">Problém s předchozím řádkem je, že `"The student cannot be found."` je pouze konstantní řetězec.</span><span class="sxs-lookup"><span data-stu-id="5c383-116">The problem with the previous line is that `"The student cannot be found."` is just a constant string.</span></span> <span data-ttu-id="5c383-117">V lokalizované aplikaci chcete mít různé zprávy v závislosti na jazykové verzi uživatele.</span><span class="sxs-lookup"><span data-stu-id="5c383-117">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="5c383-118">Tato možnost je vhodná pro [satelitní sestavení](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="5c383-118">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="5c383-119">Satelitní sestavení je knihovna DLL, která obsahuje prostředky pro určitý jazyk.</span><span class="sxs-lookup"><span data-stu-id="5c383-119">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="5c383-120">Když požádáte o konkrétní prostředky v době běhu, modul CLR tento prostředek vyhledá v závislosti na jazykové verzi uživatele.</span><span class="sxs-lookup"><span data-stu-id="5c383-120">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="5c383-121">Pokud se pro tuto jazykovou verzi nenajde žádné satelitní sestavení, použijí se prostředky výchozí jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="5c383-121">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="5c383-122">Chcete-li vytvořit lokalizované zprávy o výjimce:</span><span class="sxs-lookup"><span data-stu-id="5c383-122">To create the localized exception messages:</span></span>

1. <span data-ttu-id="5c383-123">Vytvořte novou složku s názvem *Resources* , která bude obsahovat soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="5c383-123">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="5c383-124">Přidejte do něj nový soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="5c383-124">Add a new resource file to it.</span></span> <span data-ttu-id="5c383-125">Chcete-li to provést v aplikaci Visual Studio, klikněte pravým tlačítkem myši na složku v **Průzkumník řešení**a vyberte **Přidat** > **Nový** **soubor > prostředků**.</span><span class="sxs-lookup"><span data-stu-id="5c383-125">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** > **New Item** > **Resources File**.</span></span> <span data-ttu-id="5c383-126">Pojmenujte soubor *ExceptionMessages. resx*.</span><span class="sxs-lookup"><span data-stu-id="5c383-126">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="5c383-127">Toto je výchozí soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="5c383-127">This is the default resources file.</span></span>
1. <span data-ttu-id="5c383-128">Přidejte dvojici název/hodnota pro vaši zprávu o výjimce, podobně jako na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="5c383-128">Add a name/value pair for your exception message, like the following image shows:</span></span>

   ![Přidat prostředky do výchozí jazykové verze](media/add-resources-to-default-culture.jpg)

1. <span data-ttu-id="5c383-130">Přidejte nový soubor prostředků pro francouzštinu.</span><span class="sxs-lookup"><span data-stu-id="5c383-130">Add a new resource file for French.</span></span> <span data-ttu-id="5c383-131">Pojmenujte ho *ExceptionMessages.fr-fr. resx*.</span><span class="sxs-lookup"><span data-stu-id="5c383-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="5c383-132">Znovu přidejte dvojici název/hodnota pro zprávu o výjimce, ale s francouzskou hodnotou:</span><span class="sxs-lookup"><span data-stu-id="5c383-132">Add a name/value pair for the exception message again, but with a French value:</span></span>

   ![Přidat prostředky do jazykové verze fr-FR](media/add-resources-to-fr-culture.jpg)

1. <span data-ttu-id="5c383-134">Po sestavení projektu by výstupní složka sestavení měla obsahovat složku *fr-FR* se souborem *. dll* , což je satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="5c383-134">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="5c383-135">Výjimku vyvoláte jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="5c383-135">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > <span data-ttu-id="5c383-136">Pokud je název projektu `TestProject` a soubor prostředků *ExceptionMessages. resx* se nachází ve složce *Resources* projektu, plně kvalifikovaný název souboru prostředků je `TestProject.Resources.ExceptionMessages`.</span><span class="sxs-lookup"><span data-stu-id="5c383-136">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c383-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c383-137">See also</span></span>

- [<span data-ttu-id="5c383-138">Vytvoření uživatelsky definovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="5c383-138">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="5c383-139">Vytváření satelitních sestavení pro aplikace klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="5c383-139">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="5c383-140">Base (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="5c383-140">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="5c383-141">This (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="5c383-141">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
