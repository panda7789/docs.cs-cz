---
title: "Postupy: Připojení ovládacích prvků Windows Forms k hodnotám databáze DBNull"
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
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2917288a92426c6afe9f4f97cca353c74dc954e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Postupy: Připojení ovládacích prvků Windows Forms k hodnotám databáze DBNull
Při vytvoření vazby ovládacích prvků Windows Forms ke zdroji dat a zdroj dat vrátí <xref:System.DBNull> hodnotu, můžete nahradit odpovídající hodnotu bez zpracování, formátování a analýzu událostí. <xref:System.Windows.Forms.Binding.NullValue%2A> Vlastnost převede <xref:System.DBNull> na zadaný objekt při formátování nebo analýza dat zdrojové hodnoty.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.DBNull> hodnotu ve dvou různých situacích. První ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> u vlastnosti řetězce; druhý ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> vlastnosti bitové kopie.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Typy vázané vlastnosti a <xref:System.Windows.Forms.Binding.NullValue%2A> vlastnost musí být stejná nebo dojde k chybě a ne další <xref:System.Windows.Forms.Binding.NullValue%2A> hodnoty budou zpracovány. V takovém případě nebude vyvolána výjimka.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [BindingSource – komponenta](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Postupy: zpracování chyb a výjimek, ke kterým dochází s datovou vazbou](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [Postupy: vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
