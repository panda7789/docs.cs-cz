---
title: "Postupy: Klonování tiskárny"
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
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 303cb9c1c5b6521839987a56cdc008eac0559cf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-clone-a-printer"></a>Postupy: Klonování tiskárny
Většina podniků v určitém okamžiku koupit více tiskáren stejného modelu. Obvykle to jsou nainstalovány s nastavením konfigurace prakticky identické. Instalace tiskárny může být časově náročná a chyba náchylné k chybám. <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> Obor názvů a <xref:System.Printing.PrintServer.InstallPrintQueue%2A> třídu, která se zveřejňují s [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] umožňuje okamžitě nainstalovat libovolný počet dalších tiskové fronty, které jsou klonovat z existující tiskovou frontu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je druhý tiskové fronty klonovat z existující tiskovou frontu. Druhá se liší od prvního pouze v jeho název, umístění, port a sdílený stav. Hlavní kroky tohoto postupu jsou následujícím způsobem.  
  
1.  Vytvoření <xref:System.Printing.PrintQueue> objekt pro existující tiskárny, který se bude klonovat.  
  
2.  Vytvoření <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> z <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> z <xref:System.Printing.PrintQueue>. <xref:System.Collections.DictionaryEntry.Value%2A> Vlastnost každé položky tohoto slovníku je objekt jeden z typů, které jsou odvozené z <xref:System.Printing.IndexedProperties.PrintProperty>. Existují dva způsoby, jak nastavit hodnotu položky tohoto slovníku.  
  
    -   Pomocí slovníku **odebrat** a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> metody pro odebrání položky a poté znovu přidejte s požadovanou hodnotu.  
  
    -   Pomocí slovníku <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> metoda.  
  
     Následující příklad znázorňuje obou směrech.  
  
3.  Vytvoření <xref:System.Printing.IndexedProperties.PrintBooleanProperty> objektu a nastavit jeho <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> na "IsShared" a jeho <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> k `true`.  
  
4.  Použití <xref:System.Printing.IndexedProperties.PrintBooleanProperty> objekt, který má být hodnota <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>na položku "IsShared".  
  
5.  Vytvoření <xref:System.Printing.IndexedProperties.PrintStringProperty> objektu a nastavit jeho <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> k "ShareName" a jeho <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> příslušné <xref:System.String>.  
  
6.  Použití <xref:System.Printing.IndexedProperties.PrintStringProperty> objekt, který má být hodnota <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>na položku "ShareName".  
  
7.  Vytvořte další <xref:System.Printing.IndexedProperties.PrintStringProperty> objektu a nastavit jeho <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "Místo" a jeho <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> příslušné <xref:System.String>.  
  
8.  Použít druhý <xref:System.Printing.IndexedProperties.PrintStringProperty> objekt, který má být hodnota <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>na položku "Umístění".  
  
9. Vytvoření pole <xref:System.String>s. Každá položka je název port na serveru.  
  
10. Použití <xref:System.Printing.PrintServer.InstallPrintQueue%2A> k instalaci nové tiskárny s novými hodnotami.  
  
 Příkladem je níže.  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [Dokumenty v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Tisk – přehled](../../../../docs/framework/wpf/advanced/printing-overview.md)
