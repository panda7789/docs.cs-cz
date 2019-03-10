---
title: Vizuální dědění Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
ms.openlocfilehash: e94cdc38b97f95cfe8a8504733298525c25667df
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705295"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="3e8ae-102">Vizuální dědění Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e8ae-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="3e8ae-103">V některých případech může rozhodnout, že projekt vyžaduje formuláře podobně jako ten, který jste vytvořili v předchozím projektu.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="3e8ae-104">Nebo můžete chtít vytvořit základní formulář s nastavením, jako je například vodoznaku nebo určité rozložení ovládacích prvků, které pak použijete znovu v rámci projektu, s každou iterací, který obsahuje úpravy původní šablony formuláře.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="3e8ae-105">Dědičnost formulářů umožňuje vytvoření základního formuláře a z něj dědí při zachování libovolné původní nastavení, je nutné provést změny.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="3e8ae-106">Můžete vytvořit odvozené třídy formuláře programově, nebo pomocí nástroje pro výběr vizuálního dědění.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e8ae-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3e8ae-107">In This Section</span></span>  
 [<span data-ttu-id="3e8ae-108">Postupy: Dědění formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="3e8ae-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="3e8ae-109">Poskytuje pokyny pro vytváření zděděné formuláře v kódu.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="3e8ae-110">Postupy: Dědění formulářů pomocí dialogového okna Výběr dědičnosti</span><span class="sxs-lookup"><span data-stu-id="3e8ae-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="3e8ae-111">Poskytuje pokyny pro vytvoření zděděné formuláře pomocí nástroje pro výběr dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="3e8ae-112">Účinky úpravy vzhledu základního formuláře</span><span class="sxs-lookup"><span data-stu-id="3e8ae-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="3e8ae-113">Poskytuje pokyny pro změnu základního formuláře ovládací prvky a jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="3e8ae-114">Návod: Demonstrace vizuálního dědění</span><span class="sxs-lookup"><span data-stu-id="3e8ae-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="3e8ae-115">Popisuje, jak vytvořit základní formulář Windows a zkompilovat ji do knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="3e8ae-116">Budete importovat této knihovně tříd do jiného projektu a vytvoření nového formuláře, která dědí ze základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="3e8ae-117">Postupy: Používání modifikátorů a vlastností generatemember – vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3e8ae-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="3e8ae-118">Poskytuje pokyny pro použití `GenerateMember` a `Modifiers` vlastnosti, které jsou relevantní, pokud návrhář formulářů Windows vygeneruje členské proměnné pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3e8ae-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3e8ae-119">Related Sections</span></span>  
 [<span data-ttu-id="3e8ae-120">Základní informace o dědičnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e8ae-120">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="3e8ae-121">Popisuje, jak definovat třídy jazyka Visual Basic, které slouží jako základ pro jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="3e8ae-122">class</span><span class="sxs-lookup"><span data-stu-id="3e8ae-122">class</span></span>](~/docs/csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="3e8ae-123">Popisuje C# přístup třídy, ve kterých je povolené jednoduchou dědičnost.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="3e8ae-124">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e8ae-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="3e8ae-125">Uvádí seznam běžných problémů, které vznikají u obslužných rutin událostí v zděděné komponenty</span><span class="sxs-lookup"><span data-stu-id="3e8ae-125">Lists common issues that arise with event handlers in inherited components</span></span>
