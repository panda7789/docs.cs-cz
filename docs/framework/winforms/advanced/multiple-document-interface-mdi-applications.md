---
title: Aplikace MDI (Multiple-Document Interface)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 3fa6f2517b52ecaaf4ad9db4f0de55908eac4c96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523965"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="3e84e-102">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="3e84e-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="3e84e-103">Aplikace rozhraní více dokumentů (MDI) umožňují zobrazit více dokumentů ve stejnou dobu, s každý dokument zobrazí v samostatném okně.</span><span class="sxs-lookup"><span data-stu-id="3e84e-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="3e84e-104">Aplikace MDI mají často položku nabídky okno s dílčích pro přepínání mezi windows nebo dokumenty.</span><span class="sxs-lookup"><span data-stu-id="3e84e-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e84e-105">Existují určité rozdíly chování mezi MDI formuláře a systému windows (SDI) rozhraní s jedním dokumentem ve Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3e84e-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="3e84e-106">`Opacity` Vlastnost nemá vliv na vzhled podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="3e84e-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="3e84e-107">Kromě toho <xref:System.Windows.Forms.Form.CenterToParent%2A> – metoda neovlivňuje chování podřízených formulářů MDI.</span><span class="sxs-lookup"><span data-stu-id="3e84e-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e84e-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3e84e-108">In This Section</span></span>  
 [<span data-ttu-id="3e84e-109">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="3e84e-109">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="3e84e-110">Poskytuje pokyny pro vytváření kontejneru pro více dokumentů v rámci aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="3e84e-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="3e84e-111">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="3e84e-111">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="3e84e-112">Poskytuje pokyny pro vytvoření jednoho nebo více windows, které fungují v rámci nadřazené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="3e84e-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="3e84e-113">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="3e84e-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="3e84e-114">Poskytuje pokyny pro ověření podřízeného okna, který má právě fokus, (a odesílat její obsah do schránky).</span><span class="sxs-lookup"><span data-stu-id="3e84e-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="3e84e-115">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="3e84e-115">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="3e84e-116">Poskytuje pokyny pro přenos informací do okna aktivních podřízených.</span><span class="sxs-lookup"><span data-stu-id="3e84e-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="3e84e-117">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="3e84e-117">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="3e84e-118">Poskytuje pokyny pro dlaždice, kaskádových nebo uspořádání podřízených oken MDI aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e84e-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
