---
title: Vytvoření objektového modelu
ms.date: 03/30/2017
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
ms.openlocfilehash: 68fb4ce79b5ee2277821e8a06ceab910cf35480a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247721"
---
# <a name="creating-the-object-model"></a><span data-ttu-id="18208-102">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="18208-102">Creating the Object Model</span></span>
<span data-ttu-id="18208-103">Můžete vytvořit objektový model z existující databáze a použít model ve svém výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="18208-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="18208-104">Můžete také přizpůsobit mnoho aspektů modelu a jeho chování.</span><span class="sxs-lookup"><span data-stu-id="18208-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="18208-105">Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k vytvoření objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="18208-105">If you are using Visual Studio, you can use the Object Relational Designer to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18208-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="18208-106">In This Section</span></span>  
 [<span data-ttu-id="18208-107">Postupy: Generování objektového modelu v Visual Basic neboC#</span><span class="sxs-lookup"><span data-stu-id="18208-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="18208-108">Popisuje způsob použití nástroje příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="18208-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="18208-109">Také poskytuje odkaz na Návrhář relací objektů pro uživatele sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="18208-109">Also provides a link to the Object Relational Designer for Visual Studio users</span></span>  
  
 [<span data-ttu-id="18208-110">Postupy: Generování objektového modelu jako externího souboru</span><span class="sxs-lookup"><span data-stu-id="18208-110">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="18208-111">Popisuje, jak vygenerovat soubor externího mapování namísto použití mapování založeného na atributech.</span><span class="sxs-lookup"><span data-stu-id="18208-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="18208-112">Postupy: Generování přizpůsobeného kódu úpravou souboru DBML</span><span class="sxs-lookup"><span data-stu-id="18208-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="18208-113">Popisuje, jak generovat Visual Basic nebo C# kód ze souboru s metadaty dbml.</span><span class="sxs-lookup"><span data-stu-id="18208-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="18208-114">Postupy: Ověřit soubory DBML a externí mapování</span><span class="sxs-lookup"><span data-stu-id="18208-114">How to: Validate DBML and External Mapping Files</span></span>](how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="18208-115">Popisuje, jak ověřit mapovací soubory, které jste upravili (rozšířené).</span><span class="sxs-lookup"><span data-stu-id="18208-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="18208-116">Postupy: Vytváření entit serializovatelných</span><span class="sxs-lookup"><span data-stu-id="18208-116">How to: Make Entities Serializable</span></span>](how-to-make-entities-serializable.md)  
 <span data-ttu-id="18208-117">Popisuje, jak přidat vhodné atributy pro vytváření entit serializovatelných.</span><span class="sxs-lookup"><span data-stu-id="18208-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="18208-118">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="18208-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="18208-119">Popisuje způsob použití editoru kódu k zápisu vlastního kódu mapování nebo přizpůsobení kódu, který byl automaticky vygenerován.</span><span class="sxs-lookup"><span data-stu-id="18208-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="18208-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="18208-120">Related Sections</span></span>  
 [<span data-ttu-id="18208-121">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="18208-121">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)  
 <span data-ttu-id="18208-122">Poskytuje podrobnosti o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="18208-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="18208-123">Typické postupy použití LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="18208-123">Typical Steps for Using LINQ to SQL</span></span>](typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="18208-124">Vysvětluje typické kroky, kterými se řídí implementace [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="18208-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
