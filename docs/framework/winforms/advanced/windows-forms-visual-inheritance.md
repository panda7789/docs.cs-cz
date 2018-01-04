---
title: "Vizuální dědění Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 177b3034e9afc71a8ecc899364cc4911ef42a1a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="a8ea5-102">Vizuální dědění Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8ea5-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="a8ea5-103">V některých případech může rozhodnout, že projekt vyžaduje formuláře podobně jako ten, který jste vytvořili v předchozím projektu.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="a8ea5-104">Nebo můžete chtít vytvořit základní formulář s nastavení jako vodoznak nebo určitých rozložení ovládacích prvků, který pak použijete znovu v rámci projektu, přičemž při každém opakování obsahující úpravy původní šablony formuláře.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="a8ea5-105">Dědičnost formulářů umožňuje vytvořit základní formulář a dědí při zachování aktivují původní nastavení, je nutné provést změny.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="a8ea5-106">Odvozené třídy forms můžete vytvořit prostřednictvím kódu programu, nebo pomocí nástroje pro výběr dědičnost vizuálních prvků.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8ea5-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a8ea5-107">In This Section</span></span>  
 [<span data-ttu-id="a8ea5-108">Postupy: Dědění v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8ea5-108">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 <span data-ttu-id="a8ea5-109">Poskytuje pokyny pro vytváření zděděné formuláře v kódu.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="a8ea5-110">Postupy: Dědění formulářů pomocí dialogového okna Výběr dědičnosti</span><span class="sxs-lookup"><span data-stu-id="a8ea5-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="a8ea5-111">Poskytuje pokyny pro vytvoření zděděné formuláře pomocí nástroje pro výběr dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="a8ea5-112">Účinky úpravy vzhledu základního formuláře</span><span class="sxs-lookup"><span data-stu-id="a8ea5-112">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="a8ea5-113">Poskytuje pokyny pro změnu ovládacích prvků ve formuláři základní a jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="a8ea5-114">Návod: Demonstrace vizuálního dědění</span><span class="sxs-lookup"><span data-stu-id="a8ea5-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="a8ea5-115">Popisuje postup vytvoření základního formuláře Windows a jeho kompilace do knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="a8ea5-116">Budete importovat této knihovny tříd do jiného projektu a vytvořit nový formulář, který dědí ze základní formulář.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="a8ea5-117">Postupy: Používání modifikátorů a vlastností GenerateMember</span><span class="sxs-lookup"><span data-stu-id="a8ea5-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="a8ea5-118">Poskytuje pokyny pro použití `GenerateMember` a `Modifiers` vlastnosti, které jsou relevantní, když Návrhář formulářů Windows vygeneruje členské proměnné pro součást.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8ea5-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a8ea5-119">Related Sections</span></span>  
 [<span data-ttu-id="a8ea5-120">Základní informace o dědičnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8ea5-120">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="a8ea5-121">Popisuje, jak k definování tříd jazyka Visual Basic, které slouží jako základ pro jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="a8ea5-122">class</span><span class="sxs-lookup"><span data-stu-id="a8ea5-122">class</span></span>](~/docs/csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="a8ea5-123">Popisuje postup C# tříd, ve kterých je povolena jedna dědičnost.</span><span class="sxs-lookup"><span data-stu-id="a8ea5-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="a8ea5-124">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a8ea5-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="a8ea5-125">Jsou uvedeny běžné problémy, které nastat u obslužné rutiny událostí v zděděné součásti</span><span class="sxs-lookup"><span data-stu-id="a8ea5-125">Lists common issues that arise with event handlers in inherited components</span></span>
