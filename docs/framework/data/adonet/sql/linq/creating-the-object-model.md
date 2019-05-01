---
title: Vytvoření objektového modelu
ms.date: 03/30/2017
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
ms.openlocfilehash: 7724d6e75b350e5c57f090d42ef1f49c4d3593b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032438"
---
# <a name="creating-the-object-model"></a><span data-ttu-id="b2aa0-102">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="b2aa0-102">Creating the Object Model</span></span>
<span data-ttu-id="b2aa0-103">Můžete vytvořit objektový model z existující databáze a použití modelu ve svém výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="b2aa0-104">Můžete také upravit mnoho aspektů modelu a jeho chování.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="b2aa0-105">Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vytvoření objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2aa0-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b2aa0-106">In This Section</span></span>  
 [<span data-ttu-id="b2aa0-107">Postupy: Generování objektového modelu v jazyce Visual Basic neboC#</span><span class="sxs-lookup"><span data-stu-id="b2aa0-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="b2aa0-108">Popisuje, jak pomocí nástroje příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="b2aa0-109">Také obsahuje odkaz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pro uživatele sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2aa0-109">Also provides a link to the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for Visual Studio users</span></span>  
  
 [<span data-ttu-id="b2aa0-110">Postupy: Generování objektového modelu jako externího souboru</span><span class="sxs-lookup"><span data-stu-id="b2aa0-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="b2aa0-111">Popisuje, jak generovat soubor mapování externí namísto použití založených na atributech mapování.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="b2aa0-112">Postupy: Generování přizpůsobeného kódu úpravou souboru DBML</span><span class="sxs-lookup"><span data-stu-id="b2aa0-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="b2aa0-113">Popisuje, jak generovat jazyka Visual Basic nebo C# kódu ze souboru DBML metadat.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="b2aa0-114">Postupy: Ověření DBML a externí soubory mapování</span><span class="sxs-lookup"><span data-stu-id="b2aa0-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="b2aa0-115">Popisuje, jak ověřit mapování souborů, které jste upravili (rozšířené).</span><span class="sxs-lookup"><span data-stu-id="b2aa0-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="b2aa0-116">Postupy: Nastavení entit jako serializovatelných</span><span class="sxs-lookup"><span data-stu-id="b2aa0-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="b2aa0-117">Popisuje, jak přidat příslušné atributy k nastavení entit jako serializovatelných.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="b2aa0-118">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="b2aa0-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="b2aa0-119">Popisuje, jak psát vlastní kód mapování, nebo si přizpůsobit kódu, který byl automaticky generované pomocí editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b2aa0-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b2aa0-120">Related Sections</span></span>  
 [<span data-ttu-id="b2aa0-121">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b2aa0-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="b2aa0-122">Poskytuje podrobnosti o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="b2aa0-123">Typické postupy použití LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b2aa0-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="b2aa0-124">Vysvětluje obvyklé kroky, které můžete provést k implementaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2aa0-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
