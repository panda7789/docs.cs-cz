---
title: 'Postupy: Zalomení ovládacího prvku Windows Forms pomocí ToolStripControlHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: 6335d09a89225ae1e202a781a73bfd149608f5fc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364188"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="e7b91-102">Postupy: Zalomení ovládacího prvku Windows Forms pomocí ToolStripControlHost</span><span class="sxs-lookup"><span data-stu-id="e7b91-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="e7b91-103"><xref:System.Windows.Forms.ToolStripControlHost>je navržena tak, aby povolovala hostování libovolného model Windows Forms ovládacích <xref:System.Windows.Forms.ToolStripControlHost> prvků pomocí konstruktoru nebo <xref:System.Windows.Forms.ToolStripControlHost> rozšířením sebe sama.</span><span class="sxs-lookup"><span data-stu-id="e7b91-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="e7b91-104">Ovládací prvek lze snadno zabalit rozšířením <xref:System.Windows.Forms.ToolStripControlHost> a implementací vlastností a metod, které zpřístupňují často používané vlastnosti a metody ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e7b91-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="e7b91-105">Můžete také vystavit události pro ovládací prvek na <xref:System.Windows.Forms.ToolStripControlHost> úrovni.</span><span class="sxs-lookup"><span data-stu-id="e7b91-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="e7b91-106">Hostování ovládacího prvku v ToolStripControlHost podle odvození</span><span class="sxs-lookup"><span data-stu-id="e7b91-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="e7b91-107">Rozšiřuje <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="e7b91-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="e7b91-108">Implementujte konstruktor bez parametrů, který volá konstruktor základní třídy s předáním do požadovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e7b91-108">Implement a parameterless constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="e7b91-109">Deklarujte vlastnost stejného typu jako zabalený ovládací prvek a vraťte `Control` se jako správný typ ovládacího prvku v přístupovém objektu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e7b91-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="e7b91-110">Vystavení dalších často používaných vlastností a metod zabaleného ovládacího prvku s vlastnostmi a metodami v rozšířené třídě.</span><span class="sxs-lookup"><span data-stu-id="e7b91-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="e7b91-111">Volitelně můžete přepsat <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>metody a <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> a přidat události ovládacího prvku, které chcete zveřejnit.</span><span class="sxs-lookup"><span data-stu-id="e7b91-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="e7b91-112">Poskytněte nezbytné zalamování pro události, které chcete zveřejnit.</span><span class="sxs-lookup"><span data-stu-id="e7b91-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="e7b91-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7b91-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7b91-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e7b91-114">Compiling the Code</span></span>  
  
<span data-ttu-id="e7b91-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e7b91-115">This example requires:</span></span>
  
- <span data-ttu-id="e7b91-116">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="e7b91-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b91-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7b91-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="e7b91-118">Přehled ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e7b91-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="e7b91-119">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e7b91-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="e7b91-120">Shrnutí technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e7b91-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
