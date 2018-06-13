---
title: 'Postupy: Nastavení vstupní masky'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 6f554c239e3444db5f6ac84f7994108ac70df0a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537038"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="c99f9-102">Postupy: Nastavení vstupní masky</span><span class="sxs-lookup"><span data-stu-id="c99f9-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="c99f9-103">Maskované textové pole je prvek pole rozšířené text, který podporuje deklarativní syntaxe pro přijetí nebo odmítnutí vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="c99f9-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="c99f9-104">Nastavením vlastnosti maska můžete povolená uživatelský vstup bez nutnosti psaní veškeré logiky vlastního ověřování ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c99f9-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="c99f9-105">Další informace najdete v části poznámky <xref:System.Windows.Forms.MaskedTextBox> třídy.</span><span class="sxs-lookup"><span data-stu-id="c99f9-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="c99f9-106">Nastavení vlastnosti maska ručně</span><span class="sxs-lookup"><span data-stu-id="c99f9-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="c99f9-107">Pokud jste obeznámeni s znaky, které podporuje vlastnost maska, můžete ji zadat ručně.</span><span class="sxs-lookup"><span data-stu-id="c99f9-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="c99f9-108">Souhrn znaků, které podporuje vlastnost maska, najdete v části poznámky <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c99f9-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
#### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="c99f9-109">Chcete-li ručně nastavit vlastnost maska</span><span class="sxs-lookup"><span data-stu-id="c99f9-109">To set the Mask property manually</span></span>  
  
1.  <span data-ttu-id="c99f9-110">V **návrhu** zobrazení, vyberte <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c99f9-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2.  <span data-ttu-id="c99f9-111">V **vlastnosti** okno, vyhledejte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c99f9-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3.  <span data-ttu-id="c99f9-112">Zadejte masku, který chcete.</span><span class="sxs-lookup"><span data-stu-id="c99f9-112">Type the mask that you want.</span></span> <span data-ttu-id="c99f9-113">Můžete například zadat `###`.</span><span class="sxs-lookup"><span data-stu-id="c99f9-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="c99f9-114">Pomocí dialogového okna vstupní maska</span><span class="sxs-lookup"><span data-stu-id="c99f9-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="c99f9-115">Vstupní maska dialogové okno obsahuje několik předdefinovaných vstupní masky.</span><span class="sxs-lookup"><span data-stu-id="c99f9-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="c99f9-116">Můžete také změnit předdefinované masek nebo zadejte vlastní masku ručně.</span><span class="sxs-lookup"><span data-stu-id="c99f9-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
#### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="c99f9-117">Chcete-li otevřít dialogové okno Vstupní maska</span><span class="sxs-lookup"><span data-stu-id="c99f9-117">To open the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="c99f9-118">V **návrhu** zobrazení, vyberte <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c99f9-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1.  <span data-ttu-id="c99f9-119">Klikněte na inteligentní značky otevřete **MaskedTextBox úlohy** panelu.</span><span class="sxs-lookup"><span data-stu-id="c99f9-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2.  <span data-ttu-id="c99f9-120">Klikněte na tlačítko **nastavit maska**.</span><span class="sxs-lookup"><span data-stu-id="c99f9-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="c99f9-121">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="c99f9-121">\- or -</span></span>  
  
    1.  <span data-ttu-id="c99f9-122">V **vlastnosti** vyberte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c99f9-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2.  <span data-ttu-id="c99f9-123">Klikněte na tlačítko se třemi tečkami ve sloupci Hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c99f9-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="c99f9-124">**Vstupní maska** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c99f9-124">The **Input Mask** dialog box appears.</span></span>  
  
#### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="c99f9-125">Chcete-li pomocí dialogového okna vstupní maska</span><span class="sxs-lookup"><span data-stu-id="c99f9-125">To use the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="c99f9-126">(Volitelné) Klikněte na jednu z předdefinovaných masky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="c99f9-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2.  <span data-ttu-id="c99f9-127">(Volitelné) Upravit předdefinované maska ve **maska** pole.</span><span class="sxs-lookup"><span data-stu-id="c99f9-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3.  <span data-ttu-id="c99f9-128">(Volitelné) Zadejte masku nové v **maska** pole.</span><span class="sxs-lookup"><span data-stu-id="c99f9-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="c99f9-129">To znamená, že nemáte použijte jeden z předdefinovaných masky.</span><span class="sxs-lookup"><span data-stu-id="c99f9-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c99f9-130">V poli Náhled zobrazí znaky, které uživateli se zobrazí v <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c99f9-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="c99f9-131">Tyto znaky jsou Průvodce pomoct uživateli zadat data správně.</span><span class="sxs-lookup"><span data-stu-id="c99f9-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4.  <span data-ttu-id="c99f9-132">Vyberte nebo zrušte **použití ValidatingType** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="c99f9-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="c99f9-133">**Použití ValidatingType** políčko určuje, jestli používá datový typ ověření vstupu dat uživatelem.</span><span class="sxs-lookup"><span data-stu-id="c99f9-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="c99f9-134">Další informace najdete v tématu <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c99f9-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5.  <span data-ttu-id="c99f9-135">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="c99f9-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="c99f9-136">Maska je zadána v **maska** vlastnost **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="c99f9-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c99f9-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="c99f9-137">See Also</span></span>  
 [<span data-ttu-id="c99f9-138">Návod: Práce s ovládacím prvkem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c99f9-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
