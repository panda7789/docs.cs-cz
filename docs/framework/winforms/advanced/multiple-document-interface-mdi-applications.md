---
title: Aplikace MDI (Multiple-Document Interface)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 23e0275d5e6b081ec02d669a78e8695453360637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956548"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="6b256-102">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="6b256-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="6b256-103">Aplikace MDI (Multiple Document Interface) umožňují zobrazit více dokumentů současně s každým dokumentem zobrazeným ve vlastním okně.</span><span class="sxs-lookup"><span data-stu-id="6b256-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="6b256-104">Aplikace MDI mají často položku nabídky okna s podnabídkami pro přepínání mezi okny nebo dokumenty.</span><span class="sxs-lookup"><span data-stu-id="6b256-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b256-105">Existují rozdíly v chování mezi formuláři MDI a okny rozhraní s jedním dokumentem (SDI) v model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6b256-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="6b256-106">`Opacity` Vlastnost nemá vliv na vzhled podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="6b256-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="6b256-107">Kromě toho <xref:System.Windows.Forms.Form.CenterToParent%2A> metoda nemá vliv na chování podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="6b256-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b256-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6b256-108">In This Section</span></span>  
 [<span data-ttu-id="6b256-109">Postupy: Vytvoření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="6b256-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="6b256-110">Poskytuje pokyny pro vytvoření kontejneru pro více dokumentů v rámci aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="6b256-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="6b256-111">Postupy: Vytvořit podřízené formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="6b256-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="6b256-112">Poskytuje pokyny pro vytvoření jednoho nebo více oken, které pracují v nadřazeném formuláři MDI.</span><span class="sxs-lookup"><span data-stu-id="6b256-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="6b256-113">Postupy: Zjistit aktivní podřízenou položku MDI</span><span class="sxs-lookup"><span data-stu-id="6b256-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="6b256-114">Poskytuje pokyny k ověření podřízeného okna, které má fokus (a odeslání obsahu do schránky).</span><span class="sxs-lookup"><span data-stu-id="6b256-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="6b256-115">Postupy: Odeslat data do aktivního podřízeného rozhraní MDI</span><span class="sxs-lookup"><span data-stu-id="6b256-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="6b256-116">Poskytuje pokyny pro přenos informací do aktivního podřízeného okna.</span><span class="sxs-lookup"><span data-stu-id="6b256-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="6b256-117">Postupy: Uspořádat podřízené formuláře MDI</span><span class="sxs-lookup"><span data-stu-id="6b256-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="6b256-118">Poskytuje pokyny pro dělení, kaskádové nebo uspořádávání podřízených oken aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="6b256-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
