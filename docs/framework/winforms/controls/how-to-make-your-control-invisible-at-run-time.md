---
title: 'Postupy: Skrytí vlastního ovládacího prvku za běhu'
ms.date: 03/30/2017
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
ms.openlocfilehash: 00f352e0b2c0582c45710f7e5a26e68ab7fbd944
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597788"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="9ea9b-102">Postupy: Skrytí vlastního ovládacího prvku za běhu</span><span class="sxs-lookup"><span data-stu-id="9ea9b-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="9ea9b-103">Existují situace, kdy můžete chtít vytvořit uživatelský ovládací prvek není viditelný v době běhu.</span><span class="sxs-lookup"><span data-stu-id="9ea9b-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="9ea9b-104">Například může být ovládací prvek, který je budíku neviditelné s výjimkou případů, kdy byl zvukově alarm.</span><span class="sxs-lookup"><span data-stu-id="9ea9b-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="9ea9b-105">Snadno toho dosahuje tím, že nastavíte <xref:System.Windows.Forms.Control.Visible%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9ea9b-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="9ea9b-106">Pokud <xref:System.Windows.Forms.Control.Visible%2A> vlastnost `true`, ovládací prvek se zobrazí jako obvykle.</span><span class="sxs-lookup"><span data-stu-id="9ea9b-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="9ea9b-107">Pokud `false`, bude skrytý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9ea9b-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="9ea9b-108">I když kód v ovládacím prvku přesto mohou být spuštěny při neviditelné, nebudete moci pracovat s ovládacím prvkem prostřednictvím uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9ea9b-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="9ea9b-109">Pokud chcete vytvořit skrytý ovládací prvek, který se stále reaguje na uživatelský vstup (například kliknutí myší), měli byste vytvořit transparentní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9ea9b-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="9ea9b-110">Další informace najdete v tématu [poskytuje ovládací prvek průhledné pozadí](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span><span class="sxs-lookup"><span data-stu-id="9ea9b-110">For more information, see [Giving Your Control a Transparent Background](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="9ea9b-111">Chcete-li skrytí vlastního ovládacího prvku za běhu</span><span class="sxs-lookup"><span data-stu-id="9ea9b-111">To make your control invisible at run time</span></span>  
  
1.  <span data-ttu-id="9ea9b-112">Nastavte <xref:System.Windows.Forms.Control.Visible%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="9ea9b-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ea9b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ea9b-113">See also</span></span>
- <xref:System.Windows.Forms.Control.Visible%2A>
- [<span data-ttu-id="9ea9b-114">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9ea9b-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="9ea9b-115">Postupy: Zadejte svůj ovládací prvek průhledné pozadí</span><span class="sxs-lookup"><span data-stu-id="9ea9b-115">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
