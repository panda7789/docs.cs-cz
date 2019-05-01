---
title: Aplikace MDI (Multiple-Document Interface)
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0ce7c66946d03d566b21473711cb6b3315885236
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61952045"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="51f1a-102">Aplikace MDI (Multiple-Document Interface)</span><span class="sxs-lookup"><span data-stu-id="51f1a-102">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="51f1a-103">Aplikace rozhraní více dokumentů (MDI) umožňují zobrazit více dokumentů současně, s každého dokumentu zobrazí v samostatném okně.</span><span class="sxs-lookup"><span data-stu-id="51f1a-103">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="51f1a-104">Aplikace MDI mají často položky nabídky okna s podnabídky pro přepínání mezi windows nebo dokumenty.</span><span class="sxs-lookup"><span data-stu-id="51f1a-104">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51f1a-105">Existují některé rozdíly v chování mezi formulářů MDI a interface jednoho dokumentu (SDI) systému windows ve Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="51f1a-105">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="51f1a-106">`Opacity` Vlastnost nemá vliv na vzhled podřízené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="51f1a-106">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="51f1a-107">Kromě toho <xref:System.Windows.Forms.Form.CenterToParent%2A> metoda nemá vliv na chování podřízené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="51f1a-107">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51f1a-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="51f1a-108">In This Section</span></span>  
 [<span data-ttu-id="51f1a-109">Postupy: Vytváření nadřazených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="51f1a-109">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="51f1a-110">Poskytuje pokyny pro vytvoření kontejneru pro více dokumentů v rámci aplikace MDI.</span><span class="sxs-lookup"><span data-stu-id="51f1a-110">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="51f1a-111">Postupy: Vytváření podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="51f1a-111">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="51f1a-112">Poskytuje pokyny pro vytváření jeden nebo více oken, které působí v rámci nadřazený formulář MDI.</span><span class="sxs-lookup"><span data-stu-id="51f1a-112">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="51f1a-113">Postupy: Určení podřízeného prvku aktivního MDI</span><span class="sxs-lookup"><span data-stu-id="51f1a-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="51f1a-114">Poskytuje pokyny pro ověření, který má právě fokus, podřízené okno (a odesílat její obsah do schránky.).</span><span class="sxs-lookup"><span data-stu-id="51f1a-114">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="51f1a-115">Postupy: Odesílání dat do aktivního podřízeného MDI</span><span class="sxs-lookup"><span data-stu-id="51f1a-115">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="51f1a-116">Poskytuje pokyny pro přenos informací na aktivní podřízené okno.</span><span class="sxs-lookup"><span data-stu-id="51f1a-116">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="51f1a-117">Postupy: Uspořádání podřízených formulářů MDI</span><span class="sxs-lookup"><span data-stu-id="51f1a-117">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="51f1a-118">Poskytuje pokyny pro dělení do bloků, CSS a uspořádání podřízených oken MDI aplikace.</span><span class="sxs-lookup"><span data-stu-id="51f1a-118">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
