---
title: Vytváření objektový Model
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 8686b46545699ab8c07b5d3b5f3ea26080261036
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="creating-the-object-model"></a><span data-ttu-id="baf3c-102">Vytváření objektový Model</span><span class="sxs-lookup"><span data-stu-id="baf3c-102">Creating the Object Model</span></span>
<span data-ttu-id="baf3c-103">Můžete vytvořit objektový model z existující databáze a použít model ve svém výchozím stavu.</span><span class="sxs-lookup"><span data-stu-id="baf3c-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="baf3c-104">Můžete také upravit mnoho aspektů modelu a její chování.</span><span class="sxs-lookup"><span data-stu-id="baf3c-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="baf3c-105">Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření objektu modelu.</span><span class="sxs-lookup"><span data-stu-id="baf3c-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="baf3c-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="baf3c-106">In This Section</span></span>  
 [<span data-ttu-id="baf3c-107">Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#</span><span class="sxs-lookup"><span data-stu-id="baf3c-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="baf3c-108">Popisuje, jak pomocí nástroje příkazového řádku na SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="baf3c-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="baf3c-109">Také poskytuje odkaz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pro uživatele v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="baf3c-109">Also provides a link to the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for Visual Studio users</span></span>  
  
 [<span data-ttu-id="baf3c-110">Postupy: Generování objektového modelu jako externího souboru</span><span class="sxs-lookup"><span data-stu-id="baf3c-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="baf3c-111">Popisuje, jak vytvořit soubor externí mapování místo používá mapování založené na atribut.</span><span class="sxs-lookup"><span data-stu-id="baf3c-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="baf3c-112">Postupy: Generování přizpůsobeného kódu úpravou souboru DBML</span><span class="sxs-lookup"><span data-stu-id="baf3c-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="baf3c-113">Popisuje způsob generování kódu Visual Basic a C# ze souboru DBML metadat.</span><span class="sxs-lookup"><span data-stu-id="baf3c-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="baf3c-114">Postupy: Ověření DBML a externí soubory mapování</span><span class="sxs-lookup"><span data-stu-id="baf3c-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="baf3c-115">Popisuje, jak ověřit mapování soubory, které byly upraveny (rozšířené).</span><span class="sxs-lookup"><span data-stu-id="baf3c-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="baf3c-116">Postupy: Nastavení entit jako serializovatelných</span><span class="sxs-lookup"><span data-stu-id="baf3c-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="baf3c-117">Popisuje postup přidání příslušné atributy, aby entity serializable.</span><span class="sxs-lookup"><span data-stu-id="baf3c-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="baf3c-118">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="baf3c-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="baf3c-119">Popisuje způsob použití editoru kódu napsat vlastní kód mapování, nebo upravit kód, který byl generován automaticky.</span><span class="sxs-lookup"><span data-stu-id="baf3c-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="baf3c-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="baf3c-120">Related Sections</span></span>  
 [<span data-ttu-id="baf3c-121">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="baf3c-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="baf3c-122">Poskytuje podrobnosti o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="baf3c-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="baf3c-123">Typické postupy použití LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="baf3c-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="baf3c-124">Vysvětluje obvyklé kroky, které následují k implementaci [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="baf3c-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
