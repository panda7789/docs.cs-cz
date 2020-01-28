---
title: Návrh uživatelsky přívětivého rozložení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 36ffd532b9f539107307144d25c8d9d5f8ba634a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743280"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="f0cae-102">Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci</span><span class="sxs-lookup"><span data-stu-id="f0cae-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="f0cae-103">Vytváření formulářů, které jsou připravené k lokalizaci, významně zrychluje vývoj pro mezinárodní trhy.</span><span class="sxs-lookup"><span data-stu-id="f0cae-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="f0cae-104">Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> lze použít k implementaci rozložení, která budou reagovat řádným způsobem při změně velikosti ovládacích prvků v důsledku změn v hodnotách vlastností <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0cae-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0cae-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0cae-105">Example</span></span>  
 <span data-ttu-id="f0cae-106">Tento formulář ukazuje, jak vytvořit rozložení, které se přizpůsobí při převodu zobrazených řetězcových hodnot do jiných jazyků.</span><span class="sxs-lookup"><span data-stu-id="f0cae-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="f0cae-107">Tento proces překladu se nazývá *lokalizace*.</span><span class="sxs-lookup"><span data-stu-id="f0cae-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="f0cae-108">Další informace najdete v tématu [lokalizace](../../../standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="f0cae-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="f0cae-109">Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f0cae-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="f0cae-110">Viz také [Návod: vytvoření rozložení, které upravuje proporce pro lokalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f0cae-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="f0cae-111">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="f0cae-111">Additional resources</span></span>

1. [<span data-ttu-id="f0cae-112">Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f0cae-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="f0cae-113">Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f0cae-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="f0cae-114">Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f0cae-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="f0cae-115">Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f0cae-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="f0cae-116">Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f0cae-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="f0cae-117">Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f0cae-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="f0cae-118">Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize</span><span class="sxs-lookup"><span data-stu-id="f0cae-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. <span data-ttu-id="f0cae-119">[Postupy: podpora lokalizace u model Windows Forms pomocí AutoSize a ovládacího prvku TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0cae-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>  
  
9. <span data-ttu-id="f0cae-120">[Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0cae-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f0cae-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f0cae-121">Compiling the Code</span></span>  
 <span data-ttu-id="f0cae-122">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f0cae-122">This example requires:</span></span>  
  
- <span data-ttu-id="f0cae-123">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="f0cae-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0cae-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0cae-124">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="f0cae-125">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="f0cae-125">Localization</span></span>](../../../standard/globalization-localization/localization.md)
