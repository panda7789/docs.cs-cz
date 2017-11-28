---
title: "Postupy: Načtení vlastností systémového objektu tisku bez reflexe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2f6015d25ee8868fe9b4c6dcf3bf145d413521e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a>Postupy: Načtení vlastností systémového objektu tisku bez reflexe
Chcete-li vytvořit seznam vlastností (a typy těchto vlastností) objektu pomocí reflexe můžou způsobit snížení výkonu aplikace. <xref:System.Printing.IndexedProperties> Obor názvů poskytuje prostředky k načtení těchto informací prostřednictvím reflexe.  
  
## <a name="example"></a>Příklad  
 Takto vypadají kroky tohoto postupu.  
  
1.  Vytvoření instance typu. V následujícím příkladu je typ <xref:System.Printing.PrintQueue> typ, který se dodává s [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], ale téměř shodná kódu by měla fungovat pro typy, které jsou odvozeny od <xref:System.Printing.PrintSystemObject>.  
  
2.  Vytvoření <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z tohoto typu <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>. <xref:System.Collections.DictionaryEntry.Value%2A> Vlastnost každé položky tohoto slovníku je objekt jeden z typů, které jsou odvozené z <xref:System.Printing.IndexedProperties.PrintProperty>.  
  
3.  Výčet členů slovníku. Pro každý z nich postupujte takto.  
  
4.  Přetypování nahoru hodnotu každé položky k <xref:System.Printing.IndexedProperties.PrintProperty> a použít ho k vytvoření <xref:System.Printing.IndexedProperties.PrintProperty> objektu.  
  
5.  Získat typ <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> jednotlivých <xref:System.Printing.IndexedProperties.PrintProperty> objektu.  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [Dokumenty v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Tisk – přehled](../../../../docs/framework/wpf/advanced/printing-overview.md)
