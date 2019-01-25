---
title: 'Postupy: Načtení vlastností systémového objektu tisku bez reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: b081586d201bed537c086447c4ddb116f179fbca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693250"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a>Postupy: Načtení vlastností systémového objektu tisku bez reflexe
Chcete-li vytvořit seznam vlastností (a typy těchto vlastností) na objekt pomocí reflexe můžou způsobit snížení výkonu aplikace. <xref:System.Printing.IndexedProperties> Obor názvů poskytuje prostředky k načtení těchto informací s pomocí operace reflection.  
  
## <a name="example"></a>Příklad  
 Kroky tohoto postupu jsou následující.  
  
1.  Vytvořte instanci typu. V následujícím příkladu je typ <xref:System.Printing.PrintQueue> typ, který se dodává se sadou Microsoft .NET Framework, ale téměř stejný kód by měl fungovat pro typy odvozené od <xref:System.Printing.PrintSystemObject>.  
  
2.  Vytvoření <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z tohoto typu <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>. <xref:System.Collections.DictionaryEntry.Value%2A> Vlastností pro každou položku ve slovníku je objekt jednoho z typů odvozených z <xref:System.Printing.IndexedProperties.PrintProperty>.  
  
3.  Vytvořit výčet členů slovníku. Pro každý z nich postupujte následovně.  
  
4.  Hodnota jednotlivých záznamů pro přetypování nahoru <xref:System.Printing.IndexedProperties.PrintProperty> a použijte ji k vytvoření <xref:System.Printing.IndexedProperties.PrintProperty> objektu.  
  
5.  Získat typ <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> jednotlivých <xref:System.Printing.IndexedProperties.PrintProperty> objektu.  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
- [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)
