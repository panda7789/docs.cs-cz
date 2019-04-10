---
title: 'Postupy: Nastavení vstupní masky'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 14591b313b0ba4fc2a0a30a45c693147f00050b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207536"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="8c6f3-102">Postupy: Nastavení vstupní masky</span><span class="sxs-lookup"><span data-stu-id="8c6f3-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="8c6f3-103">Maskované textové pole je vylepšené textový ovládací prvek, který podporuje deklarativní syntaxe pro přijetí nebo odmítnutí vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="8c6f3-104">Tím, že nastavíte vlastnost maska, můžete zadat povolenou uživatelský vstup bez nutnosti jakékoli vlastní ověřovací logiky ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="8c6f3-105">Další informace najdete v části poznámky <xref:System.Windows.Forms.MaskedTextBox> třídy.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="8c6f3-106">Vlastnost maska nastavení ručně</span><span class="sxs-lookup"><span data-stu-id="8c6f3-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="8c6f3-107">Pokud jste se seznámili se znaky, které podporuje vlastnost maska, můžete ji zadat ručně.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="8c6f3-108">Přehled znaky, které podporuje vlastnost maska, naleznete v části poznámky <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
#### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="8c6f3-109">Chcete-li nastavit vlastnost maska ručně</span><span class="sxs-lookup"><span data-stu-id="8c6f3-109">To set the Mask property manually</span></span>  
  
1.  <span data-ttu-id="8c6f3-110">V **návrhu** zobrazení, vyberte <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2.  <span data-ttu-id="8c6f3-111">V **vlastnosti** okna, vyhledejte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3.  <span data-ttu-id="8c6f3-112">Zadejte masku, který chcete.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-112">Type the mask that you want.</span></span> <span data-ttu-id="8c6f3-113">Zadejte například příkaz `###`.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="8c6f3-114">Pomocí dialogového okna vstupní maska</span><span class="sxs-lookup"><span data-stu-id="8c6f3-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="8c6f3-115">Vstupní maska dialogové okno obsahuje některé předdefinované vstupní masky.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="8c6f3-116">Můžete také změnit předdefinované masky nebo ručně zadejte vlastní masku.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
#### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="8c6f3-117">Chcete-li otevřít dialogové okno Vstupní maska</span><span class="sxs-lookup"><span data-stu-id="8c6f3-117">To open the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="8c6f3-118">V **návrhu** zobrazení, vyberte <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1.  <span data-ttu-id="8c6f3-119">Kliknutím na inteligentní značku otevřete **MaskedTextBox úlohy** panelu.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2.  <span data-ttu-id="8c6f3-120">Klikněte na tlačítko **nastavení masky**.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="8c6f3-121">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="8c6f3-121">\- or -</span></span>  
  
    1.  <span data-ttu-id="8c6f3-122">V **vlastnosti** okna, vyberte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2.  <span data-ttu-id="8c6f3-123">Klikněte na tlačítko se třemi tečkami v sloupec hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="8c6f3-124">**Vstupní maska** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-124">The **Input Mask** dialog box appears.</span></span>  
  
#### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="8c6f3-125">Chcete-li pomocí dialogového okna vstupní maska</span><span class="sxs-lookup"><span data-stu-id="8c6f3-125">To use the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="8c6f3-126">(Volitelné) Klikněte na jednu z předdefinovaných masky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2.  <span data-ttu-id="8c6f3-127">(Volitelné) Upravit předdefinované masky v **maska** pole.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3.  <span data-ttu-id="8c6f3-128">(Volitelné) Zadejte nový masku **maska** pole.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="8c6f3-129">To znamená, že nemáte použijte jednu z předdefinovaných masky.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c6f3-130">Zobrazí znaky, které uživateli se zobrazí v náhledu <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="8c6f3-131">Tyto znaky se tento průvodce pomůže uživateli zadat data správně.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4.  <span data-ttu-id="8c6f3-132">Zaškrtněte nebo zrušte zaškrtnutí **použít vlastnost ValidatingType** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="8c6f3-133">**Použít vlastnost ValidatingType** zaškrtávací políčko určuje, zda datový typ se používá k ověření vstupu dat uživatelem.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="8c6f3-134">Další informace najdete v tématu <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5.  <span data-ttu-id="8c6f3-135">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="8c6f3-136">Maska je zadána v **maska** vlastnost **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="8c6f3-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6f3-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c6f3-137">See also</span></span>

- [<span data-ttu-id="8c6f3-138">Návod: Práce s ovládacím prvkem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="8c6f3-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
