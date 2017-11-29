---
title: Aplikace MDI (Multiple-Document Interface)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c122931b0a00f487ddab07550913988462cfd50e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="5af41-102">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="5af41-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="5af41-103">Aplikace rozhraní více dokumentů (MDI) umožňují zobrazit více dokumentů ve stejnou dobu, s každý dokument zobrazí v samostatném okně.</span><span class="sxs-lookup"><span data-stu-id="5af41-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="5af41-104">Aplikace MDI mají často položku nabídky okno s dílčích pro přepínání mezi windows nebo dokumenty.</span><span class="sxs-lookup"><span data-stu-id="5af41-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5af41-105">Existují určité rozdíly chování mezi MDI formuláře a systému windows (SDI) rozhraní s jedním dokumentem ve Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5af41-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="5af41-106">`Opacity` Vlastnost nemá vliv na vzhled podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="5af41-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="5af41-107">Kromě toho <xref:System.Windows.Forms.Form.CenterToParent%2A> – metoda neovlivňuje chování podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="5af41-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5af41-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5af41-108">In This Section</span></span>  
 [<span data-ttu-id="5af41-109">Postupy: vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="5af41-109">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="5af41-110">Poskytuje pokyny pro vytváření kontejneru pro více dokumentů v rámci aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="5af41-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="5af41-111">Postupy: vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="5af41-111">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="5af41-112">Poskytuje pokyny pro vytvoření jednoho nebo více windows, které fungují v rámci nadřazené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="5af41-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="5af41-113">Postupy: určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="5af41-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="5af41-114">Poskytuje pokyny pro ověření podřízeného okna, který má právě fokus, (a odesílat její obsah do schránky).</span><span class="sxs-lookup"><span data-stu-id="5af41-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="5af41-115">Postupy: odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="5af41-115">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="5af41-116">Poskytuje pokyny pro přenos informací do okna aktivních podřízených.</span><span class="sxs-lookup"><span data-stu-id="5af41-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="5af41-117">Postupy: uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="5af41-117">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="5af41-118">Poskytuje pokyny pro dlaždice, kaskádových nebo uspořádání podřízených oken MDI aplikace.</span><span class="sxs-lookup"><span data-stu-id="5af41-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
