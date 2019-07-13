---
title: 'Postupy: Zjištění, jestli jde vytisknout tiskovou úlohu v této denní době'
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
ms.openlocfilehash: ee38caedc5d5a29d2221d6e5a6bf6cf74617bf8c
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859723"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Postupy: Zjištění, jestli jde vytisknout tiskovou úlohu v této denní době
Tiskové fronty nejsou vždycky k dispozici po dobu 24 hodin denně. Mají počáteční a koncový čas vlastnosti, které je možné nastavit, aby byly k dispozici v určitých časech den. Tato funkce je možné, například pro rezervaci tiskárny pro výhradní použití určitých oddělení po 17: 00. Toto oddělení by měla mít jinou frontu tiskárny, než jiných oddělení údržby použít. Fronta jiných oddělení se nastavuje nedostupnost po 17: 00, zatímco fronty pro dána oddělení může být nastaven na být vždy k dispozici.  
  
 Navíc je možné nastavit tiskové úlohy, sami bude tisknutelný pouze v rámci dané rozpětí času.  
  
 <xref:System.Printing.PrintQueue> a <xref:System.Printing.PrintSystemJobInfo> třídy v rozhraní API pro Microsoft .NET Framework umožňují vzdálené kontroly, zda danou tiskovou úlohu můžete tisknout do dané fronty v současné době.  
  
## <a name="example"></a>Příklad  
 Následující příklad je ukázka, můžete diagnostikovat problémy s tiskovou úlohou.  
  
 Existují dva hlavní kroky pro tento druh funkce následujícím způsobem.  
  
1. Přečtěte si <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti <xref:System.Printing.PrintQueue> k určení, zda aktuální čas je mezi nimi.  
  
2. Přečtěte si <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> a <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> vlastnosti <xref:System.Printing.PrintSystemJobInfo> k určení, zda aktuální čas je mezi nimi.  
  
 Ale komplikace způsobit skutečnost, že tyto vlastnosti nejsou <xref:System.DateTime> objekty. Místo toho jsou <xref:System.Int32> objekty, které je možné vyjádřit jako počet minut od půlnoci denní dobu. Kromě toho nejedná o půlnoci v aktuálním časovém pásmu, ale o půlnoci UTC (Coordinated Universal Time).  
  
 První příklad kódu představuje statickou metodu **ReportQueueAndJobAvailability**, který je předán <xref:System.Printing.PrintSystemJobInfo> a volání pomocné metody k určení, zda v současné době můžete vytisknout úlohy, a pokud ne, při tisku. Všimněte si, že <xref:System.Printing.PrintQueue> není předaný metodě. Je to proto, <xref:System.Printing.PrintSystemJobInfo> obsahuje odkaz na frontu v jeho <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> vlastnost.  
  
 Zahrnout přetížené metody podřízené **ReportAvailabilityAtThisTime** metodu, která můžete provést buď <xref:System.Printing.PrintQueue> nebo <xref:System.Printing.PrintSystemJobInfo> jako parametr. K dispozici je také **TimeConverter.ConvertToLocalHumanReadableTime**. Všechny tyto metody jsou popsané dále.  
  
 **ReportQueueAndJobAvailability** metoda začíná kontroluje se, pokud se v tuto chvíli není k dispozici fronty nebo tiskové úlohy. Pokud platí některá z nich není k dispozici, pak zkontroluje a zjistěte, jestli fronta není k dispozici. Pokud není k dispozici, metodu sestavy tuto skutečnost a čas, kdy fronty bude opět k dispozici. Potom zkontroluje úlohy a pokud je k dispozici, oznámí příště span, kdy při tisku. Nakonec metoda hlásí Nejdřívější čas, kdy můžete vytisknout úlohy. Toto je později z následujících dvakrát.  
  
- Čas, kdy je tiskovou frontu dále k dispozici.  
  
- Čas, kdy je tisková úloha dále k dispozici.  
  
 Při vytváření sestav denní dobu, <xref:System.DateTime.ToShortTimeString%2A> metodu je také volat, protože tato metoda potlačí roků, měsíců a dnů z výstupu. Dostupnost tiskovou frontu nebo tiskovou úlohu nelze omezit na konkrétní roků, měsíců nebo dokonce dny.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Dvě přetížení **ReportAvailabilityAtThisTime** metody jsou stejné s výjimkou předaný k nim, takže pouze typ <xref:System.Printing.PrintQueue> verze je uveden níže.  
  
> [!NOTE]
>  Fakt, že metody jsou stejné s výjimkou typu vyvolá na otázku, proč vzorku nevytváří žádné obecné metody **ReportAvailabilityAtThisTime\<T >** . Důvodem je, že tato metoda by mohl být omezeny na třídu, která má **StartTimeOfDay** a **UntilTimeOfDay** vlastnosti, které volá metodu, ale obecná metoda může být pouze omezené na jednotné třídy a třídy pouze společné pro <xref:System.Printing.PrintQueue> a <xref:System.Printing.PrintSystemJobInfo> v dědičnosti je strom <xref:System.Printing.PrintSystemObject> která nemá žádné takové vlastnosti.  
  
 **ReportAvailabilityAtThisTime** – metoda (uvedené v následujícím příkladu kódu) začíná inicializace <xref:System.Boolean> proměnnou sentinel `true`. Se resetuje na `false`, pokud není k dispozici do fronty.  
  
 Dále metoda zkontroluje a zjistěte, jestli začátku a "až" časy jsou identické. Pokud jsou, fronta je vždy k dispozici, a tak, aby metoda `true`.  
  
 Pokud fronta není k dispozici vždy, metoda používá statickou <xref:System.DateTime.UtcNow%2A> vlastnost k získání aktuálního času jako <xref:System.DateTime> objektu. (Jsme není nutné místního času, protože <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti představují samy o sobě v čase UTC.)  
  
 Ale tyto dvě vlastnosti nejsou <xref:System.DateTime> objekty. Jsou <xref:System.Int32>s vyjadřuje čas jako počet minut po času UTC půlnoc. Abychom měli převést naše <xref:System.DateTime> objekt minut po půlnoci. Po dokončení, která metoda jednoduše zkontroluje, můžete zjistit, zda "teď" je mezi počáteční do fronty a "časy, nastaví sentinel na hodnotu false, pokud"teď"se nenachází mezi dvěma časy a vrátí ověřovacích do".  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime** – metoda (uvedené v následujícím příkladu kódu) nepoužívá žádné metody představeny s nástrojem Microsoft .NET Framework, tedy stručný diskuse. Tato metoda má dvojitý převod úkolu: musíte trvat celé číslo vyjadřující minut po půlnoci a převést ji do čitelné čas a je nutné ji převést na místní čas. Provádí se to nejprve <xref:System.DateTime> objekt, který je nastaven na půlnoc UTC a pak používá <xref:System.DateTime.AddMinutes%2A> způsob, jak přidat dobu, po které byly předány metodě. Vrátí nový <xref:System.DateTime> vyjádření původní čas, který byl předán metodě. <xref:System.DateTime.ToLocalTime%2A> Metoda potom převede na místní čas.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
