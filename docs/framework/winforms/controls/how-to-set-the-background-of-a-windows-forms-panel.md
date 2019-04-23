---
title: 'Postupy: Nastavení pozadí panelu Windows Forms'
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
ms.openlocfilehash: 9336be2aebb10e5c0bd0bf4648cae34a3b5fe7c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300398"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="d0dee-102">Postupy: Nastavení pozadí panelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0dee-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="d0dee-103">Windows Forms <xref:System.Windows.Forms.Panel> ovládací prvek mohl zobrazit barvu pozadí a obrázek na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d0dee-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="d0dee-104"><xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost nastaví barvu pozadí pro obsažené ovládací prvky, například s popisky a přepínače.</span><span class="sxs-lookup"><span data-stu-id="d0dee-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="d0dee-105">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost není nastavená, <xref:System.Windows.Forms.Control.BackColor%2A> výběr vyplní celý panelu.</span><span class="sxs-lookup"><span data-stu-id="d0dee-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="d0dee-106">Pokud <xref:System.Windows.Forms.Control.BackgroundImage%2A> je hodnota nastavena, zobrazí se na obrázku za obsažené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d0dee-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="d0dee-107">Programové nastavení na pozadí</span><span class="sxs-lookup"><span data-stu-id="d0dee-107">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="d0dee-108">Nastavení panelu <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost na hodnotu typu <xref:System.Drawing.Color?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d0dee-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="d0dee-109">Nastavení panelu <xref:System.Windows.Forms.Control.BackgroundImage%2A> pomocí vlastnosti <xref:System.Drawing.Image.FromFile%2A> metodu <xref:System.Drawing.Image?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="d0dee-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0dee-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0dee-110">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="d0dee-111">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="d0dee-111">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="d0dee-112">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="d0dee-112">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
