---
title: "Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView"
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
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 047bc32045a9ba28d794a58d229e2f12d10e9da3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a>Postupy: Ověřování dat v ovládacím prvku Windows Forms DataGridView
Následující příklad kódu ukazuje, jak ověřit data zadaná uživatelem do <xref:System.Windows.Forms.DataGridView> ovládacího prvku. V tomto příkladu <xref:System.Windows.Forms.DataGridView> naplněný řádky z `Customers` tabulky ukázková databáze Northwind. Když uživatel upravuje buňka v `CompanyName` sloupce, jeho hodnota je testována platnost kontrolou, že to není prázdný. Pokud obslužné rutiny události pro <xref:System.Windows.Forms.DataGridView.CellValidating> událostí zjistí, že hodnota je řetězec prázdný, <xref:System.Windows.Forms.DataGridView> zabráníte uživateli ukončení buňky, dokud nebude zadán neprázdný řetězec.  
  
 Úplné vysvětlení tento příklad kódu, najdete v části [návod: ověřování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Windows.Forms a System.XML sestavení.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [Zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)
