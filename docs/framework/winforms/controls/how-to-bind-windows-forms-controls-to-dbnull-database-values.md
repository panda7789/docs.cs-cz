---
title: Svázání ovládacích prvků s hodnotami databáze DBNull
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746663"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="d47b2-102">Postupy: Připojení ovládacích prvků Windows Forms k hodnotám databáze DBNull</span><span class="sxs-lookup"><span data-stu-id="d47b2-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="d47b2-103">Když svážete model Windows Forms ovládací prvky ke zdroji dat a zdroj dat vrátí hodnotu <xref:System.DBNull>, můžete nahradit příslušnou hodnotu bez zpracování, formátování nebo analýzy událostí.</span><span class="sxs-lookup"><span data-stu-id="d47b2-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="d47b2-104">Vlastnost <xref:System.Windows.Forms.Binding.NullValue%2A> bude při formátování nebo analýze hodnot zdrojů dat převedena <xref:System.DBNull> na zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="d47b2-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d47b2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d47b2-105">Example</span></span>  
 <span data-ttu-id="d47b2-106">Následující příklad ukazuje, jak vytvořit vazby <xref:System.DBNull> hodnoty ve dvou různých situacích.</span><span class="sxs-lookup"><span data-stu-id="d47b2-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="d47b2-107">První ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> pro řetězcovou vlastnost; druhý ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> pro vlastnost obrázku.</span><span class="sxs-lookup"><span data-stu-id="d47b2-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="d47b2-108">Typy vázaných vlastností a vlastností <xref:System.Windows.Forms.Binding.NullValue%2A> musí být stejné, nebo dojde k chybě a nebudou zpracovány žádné další <xref:System.Windows.Forms.Binding.NullValue%2A> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d47b2-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="d47b2-109">V takové situaci nebude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d47b2-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d47b2-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d47b2-110">Compiling the Code</span></span>  
 <span data-ttu-id="d47b2-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d47b2-111">This example requires:</span></span>  
  
- <span data-ttu-id="d47b2-112">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="d47b2-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d47b2-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d47b2-113">See also</span></span>

- [<span data-ttu-id="d47b2-114">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="d47b2-114">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="d47b2-115">Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="d47b2-115">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="d47b2-116">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="d47b2-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
