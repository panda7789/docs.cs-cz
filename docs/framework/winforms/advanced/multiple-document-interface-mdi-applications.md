---
title: Aplikace MDI (Multiple-Document Interface)
description: Přečtěte si, jak model Windows Forms aplikace MDI (Multiple Document Interface) umožňují zobrazit více dokumentů současně s každým dokumentem zobrazeným ve vlastním okně.
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174650"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="5a4af-103">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="5a4af-103">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="5a4af-104">Aplikace MDI (Multiple Document Interface) umožňují zobrazit více dokumentů současně s každým dokumentem zobrazeným ve vlastním okně.</span><span class="sxs-lookup"><span data-stu-id="5a4af-104">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="5a4af-105">Aplikace MDI mají často položku nabídky okna s podnabídkami pro přepínání mezi okny nebo dokumenty.</span><span class="sxs-lookup"><span data-stu-id="5a4af-105">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a4af-106">Existují rozdíly v chování mezi formuláři MDI a okny rozhraní s jedním dokumentem (SDI) v model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5a4af-106">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="5a4af-107">`Opacity`Vlastnost nemá vliv na vzhled podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="5a4af-107">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="5a4af-108">Kromě toho <xref:System.Windows.Forms.Form.CenterToParent%2A> metoda nemá vliv na chování podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="5a4af-108">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a4af-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5a4af-109">In This Section</span></span>  
 [<span data-ttu-id="5a4af-110">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="5a4af-110">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="5a4af-111">Poskytuje pokyny pro vytvoření kontejneru pro více dokumentů v rámci aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="5a4af-111">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="5a4af-112">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="5a4af-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="5a4af-113">Poskytuje pokyny pro vytvoření jednoho nebo více oken, které pracují v nadřazeném formuláři MDI.</span><span class="sxs-lookup"><span data-stu-id="5a4af-113">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="5a4af-114">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="5a4af-114">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="5a4af-115">Poskytuje pokyny k ověření podřízeného okna, které má fokus (a odeslání obsahu do schránky).</span><span class="sxs-lookup"><span data-stu-id="5a4af-115">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="5a4af-116">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="5a4af-116">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="5a4af-117">Poskytuje pokyny pro přenos informací do aktivního podřízeného okna.</span><span class="sxs-lookup"><span data-stu-id="5a4af-117">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="5a4af-118">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="5a4af-118">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="5a4af-119">Poskytuje pokyny pro dělení, kaskádové nebo uspořádávání podřízených oken aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="5a4af-119">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
