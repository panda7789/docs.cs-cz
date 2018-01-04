---
title: "Postupy: Skrytí vlastního ovládacího prvku za běhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e28a682c6f3bfc52a293daebeade960c1875bb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="45728-102">Postupy: Skrytí vlastního ovládacího prvku za běhu</span><span class="sxs-lookup"><span data-stu-id="45728-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="45728-103">Existují situace, kdy můžete chtít vytvořit uživatelský ovládací prvek, který je v době běhu neviditelná.</span><span class="sxs-lookup"><span data-stu-id="45728-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="45728-104">Ovládací prvek, který je hodiny výstrahy může být například neviditelná s výjimkou případů, kdy byl zvukově na upozornění.</span><span class="sxs-lookup"><span data-stu-id="45728-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="45728-105">Toho dosahuje snadno nastavením <xref:System.Windows.Forms.Control.Visible%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="45728-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="45728-106">Pokud <xref:System.Windows.Forms.Control.Visible%2A> vlastnost je `true`, vlastní ovládací prvek se zobrazí jako normální.</span><span class="sxs-lookup"><span data-stu-id="45728-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="45728-107">Pokud `false`, bude skrytá vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="45728-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="45728-108">I když kód v vlastního ovládacího prvku může stále spustit při neviditelné, nebudete moci pracovat s ovládacím prvkem v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="45728-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="45728-109">Pokud chcete vytvořit neviditelná ovládací prvek, který stále odpoví na uživatelský vstup (například kliknutí myší), měli byste vytvořit transparentní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="45728-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="45728-110">Další informace najdete v tématu [poskytnutí vlastního ovládacího prvku průhledné pozadí](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span><span class="sxs-lookup"><span data-stu-id="45728-110">For more information, see [Giving Your Control a Transparent Background](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="45728-111">Chcete-li skrytí vlastního ovládacího prvku za běhu</span><span class="sxs-lookup"><span data-stu-id="45728-111">To make your control invisible at run time</span></span>  
  
1.  <span data-ttu-id="45728-112">Nastavte <xref:System.Windows.Forms.Control.Visible%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="45728-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="45728-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="45728-113">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [<span data-ttu-id="45728-114">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="45728-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="45728-115">Postupy: Zajištění průhledného pozadí pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="45728-115">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
