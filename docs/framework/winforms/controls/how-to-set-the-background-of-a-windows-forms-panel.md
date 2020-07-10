---
title: Nastavení pozadí panelu
description: Naučte se, jak nastavit barvu pozadí a obrázek pozadí model Windows Forms panelu pomocí návrháře.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: 109ff6184de9c79d1576207bbeb29ad939670b6f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173377"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="5cfcf-103">Postupy: Nastavení pozadí panelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5cfcf-103">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="5cfcf-104"><xref:System.Windows.Forms.Panel>Ovládací prvek model Windows Forms může zobrazit barvu pozadí i obrázek pozadí.</span><span class="sxs-lookup"><span data-stu-id="5cfcf-104">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="5cfcf-105"><xref:System.Windows.Forms.Control.BackColor%2A>Vlastnost nastavuje barvu pozadí pro obsažené ovládací prvky, jako jsou například popisky a přepínací tlačítka.</span><span class="sxs-lookup"><span data-stu-id="5cfcf-105">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="5cfcf-106">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavena, <xref:System.Windows.Forms.Control.BackColor%2A> Výběr vyplní celý panel.</span><span class="sxs-lookup"><span data-stu-id="5cfcf-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="5cfcf-107">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je vlastnost nastavena, bude obrázek zobrazen za obsažených ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="5cfcf-107">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="5cfcf-108">Programové nastavení pozadí</span><span class="sxs-lookup"><span data-stu-id="5cfcf-108">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="5cfcf-109">Nastavte <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost panelu na hodnotu typu <xref:System.Drawing.Color?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5cfcf-109">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="5cfcf-110">Nastavte <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost panelu pomocí <xref:System.Drawing.Image.FromFile%2A> metody <xref:System.Drawing.Image?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="5cfcf-110">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
    ```vb  
    ' You should replace the bolded image
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5cfcf-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cfcf-111">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="5cfcf-112">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="5cfcf-112">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="5cfcf-113">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="5cfcf-113">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
