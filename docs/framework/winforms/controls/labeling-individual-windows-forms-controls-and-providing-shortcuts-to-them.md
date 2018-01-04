---
title: "Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], access keys
- shortcuts [Windows Forms], controls
- keyboard shortcuts [Windows Forms], controls
- Windows Forms controls, labels
ms.assetid: 6eaf868c-819f-4131-8f59-048e20c286f7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e64a2a858b9506ec08beff728e23da0f817f170
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them"></a><span data-ttu-id="93f31-102">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="93f31-102">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>
<span data-ttu-id="93f31-103">Přidat do Windows Forms – ovládací prvky mít vlastnosti a metody, které se používají k další specialize uživatele prostředí.</span><span class="sxs-lookup"><span data-stu-id="93f31-103">Controls added to Windows Forms have properties and methods that are used to further specialize the user experience.</span></span> <span data-ttu-id="93f31-104">Přizpůsobení uživatelského rozhraní tak, aby vyhovovala potřebám uživatele je velmi důležité dobře navrženou pro aplikace pro Windows.</span><span class="sxs-lookup"><span data-stu-id="93f31-104">Customizing your user interface to suit the needs of the user is extremely important for well-designed Windows applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93f31-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="93f31-105">In This Section</span></span>  
 [<span data-ttu-id="93f31-106">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93f31-106">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="93f31-107">Popisuje, jak přiřadit textový popisek do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="93f31-107">Describes how to assign a text label to a control.</span></span>  
  
 [<span data-ttu-id="93f31-108">Postupy: Nastavení obrázku zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93f31-108">How to: Set the Image Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md)  
 <span data-ttu-id="93f31-109">Vysvětluje, jak nakonfigurovat ovládací prvek pro zobrazení obrázků.</span><span class="sxs-lookup"><span data-stu-id="93f31-109">Explains how to configure a control to display images.</span></span>  
  
 [<span data-ttu-id="93f31-110">Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93f31-110">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 <span data-ttu-id="93f31-111">Poskytuje informace o vytváření předdefinované klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="93f31-111">Gives information about creating predefined keyboard shortcuts.</span></span>  
  
 [<span data-ttu-id="93f31-112">Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93f31-112">Providing Accessibility Information for Controls on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md)  
 <span data-ttu-id="93f31-113">Poskytuje informace o povolení vaše ovládací prvky pro práci s usnadnění.</span><span class="sxs-lookup"><span data-stu-id="93f31-113">Gives information about enabling your controls to work with accessibility aids.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="93f31-114">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="93f31-114">Related Sections</span></span>  
 [<span data-ttu-id="93f31-115">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="93f31-115">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="93f31-116">Odkazy na další základní kroky, které můžete provést pomocí ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="93f31-116">Links to other basic things you can do with controls.</span></span>  
  
 <span data-ttu-id="93f31-117">Také najdete v části [postup: vytvoření přístup klíčů pro Windows Forms – ovládací prvky pomocí návrháře](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [postup: nastavení zobrazí Text s použitím ovládacího prvku Windows Forms návrháře](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [postupy: nastavení obrázku Zobrazí ve Windows Forms pomocí návrháře ovládacího prvku](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="93f31-117">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span></span>
