---
title: 'Postupy: vytváření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek'
description: Naučte se vytvářet uživatelsky definované výjimky s lokalizovanými zprávami výjimek.
author: Youssef1313
ms.author: ronpet
ms.date: 09/13/2019
ms.openlocfilehash: 1e5ef5658e4cb71d0689a1786494eaec57d4e7fb
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332989"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a><span data-ttu-id="0ac7d-103">Postupy: vytváření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek</span><span class="sxs-lookup"><span data-stu-id="0ac7d-103">How to: create user-defined exceptions with localized exception messages</span></span>

<span data-ttu-id="0ac7d-104">V tomto článku se naučíte, jak vytvořit uživatelsky definované výjimky, které jsou zděděné ze základní třídy <xref:System.Exception> s lokalizovanými zprávami výjimek pomocí satelitních sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-104">In this article, you will learn how to create user-defined exceptions that are inherited from the base <xref:System.Exception> class with localized exception messages using satellite assemblies.</span></span>

## <a name="create-custom-exceptions"></a><span data-ttu-id="0ac7d-105">Vytváření vlastních výjimek</span><span class="sxs-lookup"><span data-stu-id="0ac7d-105">Create custom exceptions</span></span>

<span data-ttu-id="0ac7d-106">Rozhraní .NET obsahuje mnoho různých výjimek, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-106">.NET contains many different exceptions that you can use.</span></span> <span data-ttu-id="0ac7d-107">Nicméně v některých případech, pokud žádná z nich nevyhovuje vašim potřebám, můžete vytvořit vlastní výjimky.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-107">However, in some cases when none of them meets your needs, you can create your own custom exceptions.</span></span>

<span data-ttu-id="0ac7d-108">Předpokládejme, že chcete vytvořit `StudentNotFoundException`, který obsahuje vlastnost `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-108">Let's assume you want to create a `StudentNotFoundException` that contains a `StudentName` property.</span></span>
<span data-ttu-id="0ac7d-109">Chcete-li vytvořit vlastní výjimku, použijte následující postup:</span><span class="sxs-lookup"><span data-stu-id="0ac7d-109">To create a custom exception, follow these steps:</span></span>

1. <span data-ttu-id="0ac7d-110">Vytvořte serializovatelný třídu, která dědí z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-110">Create a serializable class that inherits from <xref:System.Exception>.</span></span> <span data-ttu-id="0ac7d-111">Název třídy by měl končit "výjimku":</span><span class="sxs-lookup"><span data-stu-id="0ac7d-111">The class name should end in "Exception":</span></span>

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. <span data-ttu-id="0ac7d-112">Přidejte výchozí konstruktory:</span><span class="sxs-lookup"><span data-stu-id="0ac7d-112">Add the default constructors:</span></span>

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

1. <span data-ttu-id="0ac7d-113">Definujte jakékoli další vlastnosti a konstruktory:</span><span class="sxs-lookup"><span data-stu-id="0ac7d-113">Define any additional properties and constructors:</span></span>

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

## <a name="create-localized-exception-messages"></a><span data-ttu-id="0ac7d-114">Vytvoření lokalizovaných zpráv výjimek</span><span class="sxs-lookup"><span data-stu-id="0ac7d-114">Create localized exception messages</span></span>

<span data-ttu-id="0ac7d-115">Vytvořili jste vlastní výjimku a můžete ji vyvolat kdekoli pomocí kódu podobného následujícímu:</span><span class="sxs-lookup"><span data-stu-id="0ac7d-115">You have created a custom exception, and you can throw it anywhere with code like the following:</span></span>

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

<span data-ttu-id="0ac7d-116">Problémem s předchozím řádkem je to, že student nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-116">The problem with the previous line is that "The student cannot be found."</span></span> <span data-ttu-id="0ac7d-117">je pouze konstantní řetězec.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-117">is just a constant string.</span></span> <span data-ttu-id="0ac7d-118">V lokalizované aplikaci chcete mít různé zprávy v závislosti na jazykové verzi uživatele.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-118">In a localized application, you want to have different messages depending on user culture.</span></span>
<span data-ttu-id="0ac7d-119">Tato možnost je vhodná pro [satelitní sestavení](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="0ac7d-119">[Satellite Assemblies](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) are a good way to do that.</span></span> <span data-ttu-id="0ac7d-120">Satelitní sestavení je knihovna DLL, která obsahuje prostředky pro určitý jazyk.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-120">A satellite assembly is a .dll that contains resources for a specific language.</span></span> <span data-ttu-id="0ac7d-121">Když požádáte o konkrétní prostředky v době běhu, modul CLR tento prostředek vyhledá v závislosti na jazykové verzi uživatele.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-121">When you ask for a specific resources at run time, the CLR finds that resource depending on user culture.</span></span> <span data-ttu-id="0ac7d-122">Pokud se pro tuto jazykovou verzi nenajde žádné satelitní sestavení, použijí se prostředky výchozí jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-122">If no satellite assembly is found for that culture, the resources of the default culture are used.</span></span>

<span data-ttu-id="0ac7d-123">Chcete-li vytvořit lokalizované zprávy o výjimce:</span><span class="sxs-lookup"><span data-stu-id="0ac7d-123">To create the localized exception messages:</span></span>

1. <span data-ttu-id="0ac7d-124">Vytvořte novou složku s názvem *Resources* , která bude obsahovat soubory prostředků.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-124">Create a new folder named *Resources* to hold the resource files.</span></span>
1. <span data-ttu-id="0ac7d-125">Přidejte do něj nový soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-125">Add a new resource file to it.</span></span> <span data-ttu-id="0ac7d-126">Provedete to tak, že v aplikaci Visual Studio kliknete pravým tlačítkem na složku v **Průzkumník řešení**a vyberete **přidat** **soubor prostředků** -> **nové položky** -> .</span><span class="sxs-lookup"><span data-stu-id="0ac7d-126">To do that in Visual Studio, right-click the folder in **Solution Explorer**, and select **Add** -> **New Item** -> **Resources File**.</span></span> <span data-ttu-id="0ac7d-127">Pojmenujte soubor *ExceptionMessages. resx*.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-127">Name the file *ExceptionMessages.resx*.</span></span> <span data-ttu-id="0ac7d-128">Toto je výchozí soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-128">This is the default resources file.</span></span>
1. <span data-ttu-id="0ac7d-129">Přidejte dvojici název/hodnota pro vaši zprávu o výjimce, podobně jako na následujícím obrázku: @no__t 0Add prostředky k výchozí jazykové verzi @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="0ac7d-129">Add a name/value pair for your exception message, like the following image shows: ![Add resources to the default culture](media/add-resources-to-default-culture.jpg)</span></span>
1. <span data-ttu-id="0ac7d-130">Přidejte nový soubor prostředků pro francouzštinu.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-130">Add a new resource file for French.</span></span> <span data-ttu-id="0ac7d-131">Pojmenujte ho *ExceptionMessages.fr-fr. resx*.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-131">Name it *ExceptionMessages.fr-FR.resx*.</span></span>
1. <span data-ttu-id="0ac7d-132">Znovu přidejte dvojici název/hodnota pro zprávu o výjimce, ale s francouzskou hodnotou: prostředky ![Add do jazykové verze fr-FR @ no__t-1</span><span class="sxs-lookup"><span data-stu-id="0ac7d-132">Add a name/value pair for the exception message again, but with a French value: ![Add resources to the fr-FR culture](media/add-resources-to-fr-culture.jpg)</span></span>
1. <span data-ttu-id="0ac7d-133">Po sestavení projektu by výstupní složka sestavení měla obsahovat složku *fr-FR* se souborem *. dll* , což je satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-133">After you build the project, the build output folder should contain the *fr-FR* folder with a *.dll* file, which is the satellite assembly.</span></span>
1. <span data-ttu-id="0ac7d-134">Výjimku vyvoláte jako následující kód:</span><span class="sxs-lookup"><span data-stu-id="0ac7d-134">You throw the exception with code like the following:</span></span>

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > <span data-ttu-id="0ac7d-135">Pokud je název projektu `TestProject` a soubor prostředků *ExceptionMessages. resx* se nachází ve složce *Resources* projektu, plně kvalifikovaný název souboru prostředků je `TestProject.Resources.ExceptionMessages`.</span><span class="sxs-lookup"><span data-stu-id="0ac7d-135">If the project name is `TestProject` and the resource file *ExceptionMessages.resx* resides in the *Resources* folder of the project, the fully qualified name of the resource file is `TestProject.Resources.ExceptionMessages`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ac7d-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ac7d-136">See also</span></span>

- [<span data-ttu-id="0ac7d-137">Vytvoření uživatelsky definovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="0ac7d-137">How to create user-defined exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="0ac7d-138">Vytváření satelitních sestavení pro aplikace klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="0ac7d-138">Creating Satellite Assemblies for Desktop Apps</span></span>](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="0ac7d-139">Base (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="0ac7d-139">base (C# Reference)</span></span>](../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="0ac7d-140">This (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="0ac7d-140">this (C# Reference)</span></span>](../../csharp/language-reference/keywords/this.md)
