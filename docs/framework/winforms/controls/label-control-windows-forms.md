---
title: "Ovládací prvek Popisek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Label control [Windows Forms]
- labels
- LinkLabel control [Windows Forms]
ms.assetid: 2028bbe3-ffe2-43e8-8ae3-dec759d2ecec
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 90a870c71bc7e5d853049d363c27a29d00be3f6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="label-control-windows-forms"></a><span data-ttu-id="83fae-102">Ovládací prvek Popisek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="83fae-102">Label Control (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="83fae-103"><xref:System.Windows.Forms.ToolStripLabel> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.Label> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="83fae-103">The <xref:System.Windows.Forms.ToolStripLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.Label> control.</span></span> <span data-ttu-id="83fae-104">Můžete použít <xref:System.Windows.Forms.ToolStripLabel> s další nové ovládací prvky, jako <xref:System.Windows.Forms.ToolStripDropDown>.</span><span class="sxs-lookup"><span data-stu-id="83fae-104">You can use the <xref:System.Windows.Forms.ToolStripLabel> with other new controls such as the <xref:System.Windows.Forms.ToolStripDropDown>.</span></span> <span data-ttu-id="83fae-105">Ale <xref:System.Windows.Forms.Label> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="83fae-105">However, the <xref:System.Windows.Forms.Label> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="83fae-106">Windows Forms <xref:System.Windows.Forms.Label> ovládací prvky slouží k zobrazení textu nebo obrázků, které uživatel nemůže upravovat.</span><span class="sxs-lookup"><span data-stu-id="83fae-106">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="83fae-107">Slouží k identifikaci objektů ve formuláři – zadejte popis co určité ovládacího prvku budou dělat, když klikli, například nebo zobrazit informace v reakci na události spuštění nebo proces v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="83fae-107">They are used to identify objects on a form—to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="83fae-108">Protože <xref:System.Windows.Forms.Label> ovládacího prvku nelze aktivovat, můžete použít také k vytváření přístupových klíčů pro další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="83fae-108">Because the <xref:System.Windows.Forms.Label> control cannot receive focus, it can also be used to create access keys for other controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83fae-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="83fae-109">In This Section</span></span>  
 [<span data-ttu-id="83fae-110">Přehled ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="83fae-110">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 <span data-ttu-id="83fae-111">Vysvětluje, co je tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="83fae-111">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="83fae-112">Postupy: vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label</span><span class="sxs-lookup"><span data-stu-id="83fae-112">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 <span data-ttu-id="83fae-113">Popisuje, jak používat k definování přístupový klíč pro další ovládací prvek popisek.</span><span class="sxs-lookup"><span data-stu-id="83fae-113">Describes how to use a label to define an access key for another control.</span></span>  
  
 [<span data-ttu-id="83fae-114">Postupy: velikost Windows Forms – ovládací prvek popisek podle obsahu</span><span class="sxs-lookup"><span data-stu-id="83fae-114">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 <span data-ttu-id="83fae-115">Vysvětluje, úprava velikosti ovládacího prvku popisek pro titulek.</span><span class="sxs-lookup"><span data-stu-id="83fae-115">Explains adjusting the size of a label control for its caption.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="83fae-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="83fae-116">Reference</span></span>  
 <xref:System.Windows.Forms.Label>  
 <span data-ttu-id="83fae-117">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="83fae-117">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="83fae-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="83fae-118">Related Sections</span></span>  
 [<span data-ttu-id="83fae-119">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="83fae-119">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="83fae-120">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="83fae-120">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
