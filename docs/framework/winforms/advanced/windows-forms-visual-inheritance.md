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
ms.openlocfilehash: 11a90615938da9e7dda5e05c55546918ccde137d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957106"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="b3964-102">Vizuální dědění Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3964-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="b3964-103">V některých případech se můžete rozhodnout, že projekt volá pro formulář podobný tomu, který jste vytvořili v předchozím projektu.</span><span class="sxs-lookup"><span data-stu-id="b3964-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="b3964-104">Nebo můžete chtít vytvořit základní formulář s nastavením, jako je například vodoznak nebo určité rozložení ovládacích prvků, které pak použijete v rámci projektu, přičemž každá iterace obsahuje změny původní šablony formuláře.</span><span class="sxs-lookup"><span data-stu-id="b3964-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="b3964-105">Dědičnost formulářů umožňuje vytvořit základní formulář a pak z něj dědit a provádět úpravy a přitom zachovat libovolná původní nastavení, která potřebujete.</span><span class="sxs-lookup"><span data-stu-id="b3964-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="b3964-106">Formuláře odvozené třídy můžete vytvořit programově nebo pomocí výběru dědičnosti vizuálního rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3964-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3964-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b3964-107">In This Section</span></span>  
 [<span data-ttu-id="b3964-108">Postupy: Zdědit model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b3964-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="b3964-109">Poskytuje pokyny pro vytváření zděděných formulářů v kódu.</span><span class="sxs-lookup"><span data-stu-id="b3964-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="b3964-110">Postupy: Dědění formulářů pomocí dialogového okna pro výběr dědičnosti</span><span class="sxs-lookup"><span data-stu-id="b3964-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="b3964-111">Poskytuje pokyny pro vytváření zděděných formulářů pomocí výběru dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="b3964-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="b3964-112">Účinky úpravy vzhledu základního formuláře</span><span class="sxs-lookup"><span data-stu-id="b3964-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="b3964-113">Poskytuje pokyny pro změnu základního ovládacího prvku formuláře a jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="b3964-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="b3964-114">Návod: Demonstrace vizuálního dědění</span><span class="sxs-lookup"><span data-stu-id="b3964-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="b3964-115">Popisuje, jak vytvořit základní formulář Windows a zkompilovat ho do knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="b3964-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="b3964-116">Tuto knihovnu tříd naimportujete do jiného projektu a vytvoříte nový formulář, který bude dědit ze základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="b3964-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="b3964-117">Postupy: Použití modifikátorů a vlastností GenerateMember</span><span class="sxs-lookup"><span data-stu-id="b3964-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="b3964-118">Poskytuje pokyny pro použití `GenerateMember` vlastností a `Modifiers` , které jsou relevantní, pokud Návrhář formulářů generuje členskou proměnnou pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="b3964-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b3964-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b3964-119">Related Sections</span></span>  
 [<span data-ttu-id="b3964-120">Základy dědičnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3964-120">Inheritance basics (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="b3964-121">Popisuje, jak definovat Visual Basic třídy, které slouží jako základ pro jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="b3964-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="b3964-122">class</span><span class="sxs-lookup"><span data-stu-id="b3964-122">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="b3964-123">Popisuje C# přístup tříd, ve kterých je povolena jednoduchá dědičnost.</span><span class="sxs-lookup"><span data-stu-id="b3964-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="b3964-124">Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3964-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="b3964-125">Zobrazí běžné problémy, které vznikají u obslužných rutin událostí ve zděděných součástech.</span><span class="sxs-lookup"><span data-stu-id="b3964-125">Lists common issues that arise with event handlers in inherited components</span></span>
