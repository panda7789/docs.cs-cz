---
title: 'Postupy: Nastavení vstupní masky'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949138"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="3a0f8-102">Postupy: Nastavení vstupní masky</span><span class="sxs-lookup"><span data-stu-id="3a0f8-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="3a0f8-103">Ovládací prvek maskovaná textová pole je vylepšený ovládací prvek textového pole, který podporuje deklarativní syntaxi pro přijetí nebo odmítnutí vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="3a0f8-104">Nastavením vlastnosti maska můžete zadat povolený vstup uživatele bez psaní jakékoli vlastní ověřovací logiky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="3a0f8-105">Další informace naleznete v oddílu <xref:System.Windows.Forms.MaskedTextBox> poznámky třídy.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="3a0f8-106">Ruční nastavení vlastnosti masky</span><span class="sxs-lookup"><span data-stu-id="3a0f8-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="3a0f8-107">Pokud jste obeznámeni se znaky, které vlastnost Mask podporuje, můžete ji zadat ručně.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="3a0f8-108">Souhrn znaků, které vlastnost Mask podporuje, naleznete v části <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> poznámky v této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="3a0f8-109">Ruční nastavení vlastnosti masky</span><span class="sxs-lookup"><span data-stu-id="3a0f8-109">To set the Mask property manually</span></span>  
  
1. <span data-ttu-id="3a0f8-110">V zobrazení **Návrh** vyberte <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2. <span data-ttu-id="3a0f8-111">V okně **vlastnosti** vyhledejte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3. <span data-ttu-id="3a0f8-112">Zadejte masku, kterou chcete.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-112">Type the mask that you want.</span></span> <span data-ttu-id="3a0f8-113">Zadejte například příkaz `###`.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="3a0f8-114">Použití dialogového okna vstupní maska</span><span class="sxs-lookup"><span data-stu-id="3a0f8-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="3a0f8-115">Dialogové okno vstupní maska poskytuje některé předdefinované vstupní masky.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="3a0f8-116">Můžete také změnit předdefinované masky nebo zadat vlastní masku ručně.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="3a0f8-117">Otevření dialogového okna vstupní maska</span><span class="sxs-lookup"><span data-stu-id="3a0f8-117">To open the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="3a0f8-118">V zobrazení **Návrh** vyberte <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1. <span data-ttu-id="3a0f8-119">Kliknutím na inteligentní značku otevřete panel **úlohy ovládacím MaskedTextBox** .</span><span class="sxs-lookup"><span data-stu-id="3a0f8-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2. <span data-ttu-id="3a0f8-120">Klikněte na **nastavit masku**.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="3a0f8-121">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="3a0f8-121">\- or -</span></span>  
  
    1. <span data-ttu-id="3a0f8-122">V okně **vlastnosti** vyberte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2. <span data-ttu-id="3a0f8-123">Klikněte na tlačítko se třemi tečkami ve sloupci Hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="3a0f8-124">Zobrazí se dialogové okno **vstupní maska** .</span><span class="sxs-lookup"><span data-stu-id="3a0f8-124">The **Input Mask** dialog box appears.</span></span>  
  
### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="3a0f8-125">Použití dialogového okna vstupní maska</span><span class="sxs-lookup"><span data-stu-id="3a0f8-125">To use the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="3a0f8-126">Volitelné V seznamu klikněte na jednu z předdefinovaných masek.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2. <span data-ttu-id="3a0f8-127">Volitelné Upravte předdefinovanou masku v poli **Maska** .</span><span class="sxs-lookup"><span data-stu-id="3a0f8-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3. <span data-ttu-id="3a0f8-128">Volitelné Do pole **Maska** zadejte novou masku.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="3a0f8-129">To znamená, že nemusíte používat jednu z předdefinovaných masek.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3a0f8-130">V poli Náhled se zobrazí znaky, které uživatel vidí v <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="3a0f8-131">Tyto znaky jsou vodítkem, který uživatelům pomůže správně zadat data.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4. <span data-ttu-id="3a0f8-132">Zaškrtněte nebo zrušte zaškrtnutí políčka **Use ValidatingType** .</span><span class="sxs-lookup"><span data-stu-id="3a0f8-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="3a0f8-133">Zaškrtávací políčko **použít ValidatingType** určuje, zda datový typ slouží k ověření datového vstupu uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="3a0f8-134">Další informace najdete v tématu <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5. <span data-ttu-id="3a0f8-135">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="3a0f8-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="3a0f8-136">Maska se zadává do vlastnosti **Maska** v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="3a0f8-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a0f8-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a0f8-137">See also</span></span>

- [<span data-ttu-id="3a0f8-138">Návod: Práce s ovládacím prvkem ovládacím MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="3a0f8-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
