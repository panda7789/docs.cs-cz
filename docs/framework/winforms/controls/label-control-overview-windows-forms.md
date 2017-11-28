---
title: "Přehled ovládacího prvku Popisek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f55cfb6afa8ad533aac84b391a7cd6fef83d72d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="label-control-overview-windows-forms"></a><span data-ttu-id="75257-102">Přehled ovládacího prvku Popisek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="75257-102">Label Control Overview (Windows Forms)</span></span>
<span data-ttu-id="75257-103">Windows Forms <xref:System.Windows.Forms.Label> ovládací prvky slouží k zobrazení textu nebo obrázků, které uživatel nemůže upravovat.</span><span class="sxs-lookup"><span data-stu-id="75257-103">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="75257-104">Slouží k identifikaci objektů ve formuláři – zadejte popis co určité ovládacího prvku budou dělat, když klikli, například nebo zobrazit informace v reakci na události spuštění nebo proces v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="75257-104">They are used to identify objects on a form — to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="75257-105">Můžete například použít popisky Pokud chcete přidat popisný titulky textová pole, seznamy, pole se seznamem a tak dále.</span><span class="sxs-lookup"><span data-stu-id="75257-105">For example, you can use labels to add descriptive captions to text boxes, list boxes, combo boxes, and so on.</span></span> <span data-ttu-id="75257-106">Můžete také psát kód, který změní text zobrazený popiskem v reakci na události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="75257-106">You can also write code that changes the text displayed by a label in response to events at run time.</span></span> <span data-ttu-id="75257-107">Například pokud vaše aplikace trvá několik minut, než se zpracovat změnu, můžete zobrazit zprávu o stavu zpracování v popisku.</span><span class="sxs-lookup"><span data-stu-id="75257-107">For example, if your application takes a few minutes to process a change, you can display a processing-status message in a label.</span></span>  
  
## <a name="working-with-the-label-control"></a><span data-ttu-id="75257-108">Práce s ovládacím prvkem popisek</span><span class="sxs-lookup"><span data-stu-id="75257-108">Working with the Label Control</span></span>  
 <span data-ttu-id="75257-109">Protože <xref:System.Windows.Forms.Label> řízení nemůže získat fokus, můžete použít také k vytváření přístupových klíčů pro další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="75257-109">Because the <xref:System.Windows.Forms.Label> control cannot receive the focus, it can also be used to create access keys for other controls.</span></span> <span data-ttu-id="75257-110">Přístupový klíč umožňuje uživateli vybrat další ovládací prvek stisknutím klávesy ALT přístupovým klíčem.</span><span class="sxs-lookup"><span data-stu-id="75257-110">An access key allows a user to select the other control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="75257-111">Další informace najdete v tématu [vytváření přístup klíčů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) a [postupy: vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span><span class="sxs-lookup"><span data-stu-id="75257-111">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) and [How to: Create Access Keys with Windows Forms Label Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span></span>  
  
 <span data-ttu-id="75257-112">Je součástí titulek zobrazený v popisku <xref:System.Windows.Forms.Label.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="75257-112">The caption displayed in the label is contained in the <xref:System.Windows.Forms.Label.Text%2A> property.</span></span> <span data-ttu-id="75257-113"><xref:System.Windows.Forms.Label.TextAlign%2A> Vlastnost můžete nastavit zarovnání textu v rámci popisku.</span><span class="sxs-lookup"><span data-stu-id="75257-113">The <xref:System.Windows.Forms.Label.TextAlign%2A> property allows you to set the alignment of the text within the label.</span></span> <span data-ttu-id="75257-114">Další informace najdete v tématu [postupy: nastavení zobrazí Text pomocí ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="75257-114">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75257-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="75257-115">See Also</span></span>  
 <xref:System.Windows.Forms.Label>  
 [<span data-ttu-id="75257-116">Postupy: velikost Windows Forms – ovládací prvek popisek podle obsahu</span><span class="sxs-lookup"><span data-stu-id="75257-116">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="75257-117">Postupy: vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label</span><span class="sxs-lookup"><span data-stu-id="75257-117">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)
