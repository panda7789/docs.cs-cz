---
title: 'Postupy: Zjištění, zda lze vytisknout tiskovou úlohu v této denní době'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: e5ea5ad3bcb10bfbc091f0b5852ee181a2c3fa8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548032"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Postupy: Zjištění, zda lze vytisknout tiskovou úlohu v této denní době
Tiskové fronty nejsou vždy k dispozici po dobu 24 hodin denně. Mají počáteční a koncové vlastnosti doby, které lze nastavit, aby byly k dispozici v určitých časech den. Tuto funkci můžete použít například tak, aby vyhradil tiskárny pro výhradní použití určitých oddělení po 17: 00. Oddělení by měla mít jiné fronty obsluhy tiskárny než jiných oddělení použijte. Fronta jiných oddělení by být nastaveny na k dispozici po 17: 00, zatímco fronty pro favored oddělení může být nastaveny na vždy k dispozici.  
  
 Tiskové úlohy, sami kromě toho může být nastaveny na tisknutelná pouze v rámci dané rozpětí času.  
  
 <xref:System.Printing.PrintQueue> a <xref:System.Printing.PrintSystemJobInfo> třídy vystavený v [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Microsoft .NET Framework umožňují vzdáleně kontroly, zda danou tiskovou úlohu můžete vytisknout v dané frontě v aktuálním čase.  
  
## <a name="example"></a>Příklad  
 Následující příklad je ukázka, která lze diagnostikovat problémy s tiskové úlohy.  
  
 Existují dva hlavní kroky pro tento typ funkce následujícím způsobem.  
  
1.  Pro čtení <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti <xref:System.Printing.PrintQueue> k určení, zda je aktuální čas mezi nimi.  
  
2.  Pro čtení <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> a <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> vlastnosti <xref:System.Printing.PrintSystemJobInfo> k určení, zda je aktuální čas mezi nimi.  
  
 Ale komplikace vzniknout ze skutečnosti, že tyto vlastnosti nejsou <xref:System.DateTime> objekty. Místo toho jsou <xref:System.Int32> objekty, které express denní dobu, jako je počet minut od půlnoci. Kromě toho tento není půlnoci v aktuální časové pásmo, ale půlnoci času UTC (Coordinated Universal Time).  
  
 V prvním příkladu kódu představuje statickou metodu **ReportQueueAndJobAvailability**, který je předán <xref:System.Printing.PrintSystemJobInfo> a volání pomocné metody pro určení, zda v současné době můžete vytisknout úlohy, a pokud ne, při tisku. Všimněte si, že <xref:System.Printing.PrintQueue> není předaný metodě. Důvodem je, že <xref:System.Printing.PrintSystemJobInfo> obsahuje odkaz na frontu v jeho <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> vlastnost.  
  
 Podřízené metody patří přetížené **ReportAvailabilityAtThisTime** metoda, která může mít buď <xref:System.Printing.PrintQueue> nebo <xref:System.Printing.PrintSystemJobInfo> jako parametr. K dispozici je také **TimeConverter.ConvertToLocalHumanReadableTime**. Všechny tyto metody jsou popsané dále.  
  
 **ReportQueueAndJobAvailability** metoda začne kontrolou, pokud chcete zobrazit, pokud v tuto chvíli není k dispozici fronta nebo tiskové úlohy. Pokud některá z nich není k dispozici, pak zkontroluje, pokud není k dispozici fronty. Pokud není k dispozici, metoda sestavy tuto skutečnost a čas, kdy fronty bude opět k dispozici. Pak zkontroluje projekt a pokud je k dispozici, oznámí příštím span, kdy se při tisku. Nakonec metodu hlásí Nejdřívější čas, kdy můžete vytisknout úlohy. Toto je novější následujících dvakrát.  
  
-   Čas, kdy je v tiskové frontě dále k dispozici.  
  
-   Čas, kdy je daná tisková úloha dále k dispozici.  
  
 Při hlášení denní dobu, <xref:System.DateTime.ToShortTimeString%2A> metoda se označuje taky jako, protože tato metoda potlačí let, měsíce a dny z výstupu. Dostupnost tiskovou frontu nebo tiskové úlohy nelze omezit na konkrétní let, měsíců nebo dní.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Dva přetížení **ReportAvailabilityAtThisTime** metoda jsou identické s výjimkou typu předán do je, takže jenom <xref:System.Printing.PrintQueue> verze je uveden níže.  
  
> [!NOTE]
>  Skutečnost, že jsou identické s výjimkou typu metody vyvolává otázku, proč ukázku nevytvoří obecná metoda **ReportAvailabilityAtThisTime\<T >**. Důvodem je, že tato metoda by mohl být omezen na třídu, která má **StartTimeOfDay** a **UntilTimeOfDay** vlastnosti, které volá metodu, ale obecná metoda může být pouze omezené jednotné třídy a třídy pouze společné pro objekty <xref:System.Printing.PrintQueue> a <xref:System.Printing.PrintSystemJobInfo> v dědičnosti stromu je <xref:System.Printing.PrintSystemObject> který nemá žádné tyto vlastnosti.  
  
 **ReportAvailabilityAtThisTime** – metoda (uvedené v následujícím příkladu kódu) začne podle inicializace <xref:System.Boolean> sentinel proměnnou `true`. Bude obnovena do `false`, pokud není k dispozici fronty.  
  
 V dalším kroku metoda zkontroluje, pokud se spuštění a "dokud" časy jsou identické. Pokud ano, fronty je vždy k dispozici, a proto vrátí metoda `true`.  
  
 Pokud fronta není k dispozici vždy, metoda používá statickou <xref:System.DateTime.UtcNow%2A> vlastnost, která má získat aktuální čas jako <xref:System.DateTime> objektu. (Jsme není nutné místního času, protože <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> sami vlastnosti jsou ve formátu času UTC.)  
  
 Však tyto dvě vlastnosti nejsou <xref:System.DateTime> objekty. Jsou <xref:System.Int32>s vyjadřující čas jako počet minut po času UTC půlnoci. Abychom měli převést naše <xref:System.DateTime> objekt minut po půlnoci. Pokud, se provádí, zkontroluje tato metoda jednoduše můžete zjistit, zda "teď" je mezi fronty spuštění a "časy, nastaví sentinel na hodnotu false, pokud"teď"není mezi dvěma časy a vrátí sentinel do".  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime** – metoda (uvedené v následujícím příkladu kódu) nepoužívá žádné metody zavedené rozhraní Microsoft .NET Framework, takže diskuse je stručný. Metoda je úkol dvojitý převod: musí trvat celé vyjadřující minut po půlnoci a převeďte ho na čitelná pro člověka čas a je nutné ji převést na místní čas. Provádí se to tak, že první vytvoříte <xref:System.DateTime> objekt, který je nastavenou na půlnoc UTC a pak se používá <xref:System.DateTime.AddMinutes%2A> metody přidat minut, které byly předány metodě. Vrátí nový <xref:System.DateTime> vyjadřující původní čas, který byl předaný metodě. <xref:System.DateTime.ToLocalTime%2A> Metoda potom převede na místní čas.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.Printing.PrintQueue>  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)
