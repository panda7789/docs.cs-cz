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
ms.openlocfilehash: 859dc75169e443d07361951692a428507886fa2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947799"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Postupy: Zjištění, jestli jde vytisknout tiskovou úlohu v této denní době
Tiskové fronty nejsou vždy k dispozici po dobu 24 hodin denně. Mají vlastnosti počáteční a koncového času, které je možné nastavit tak, aby byly v určitou dobu nedostupné. Tato funkce se dá použít například k vyhrazení tiskárny pro výhradní použití určitého oddělení po dobu 5 hodin. Toto oddělení by mělo jinou frontu, která obsluhuje tiskárnu, než jiné oddělení používají. Fronta pro ostatní oddělení se nastaví jako nedostupná po dobu 5 hodin, zatímco fronta pro Upřednostněné oddělení by mohla být na všech místech k dispozici.  
  
 Tisk samotných úloh se navíc dá nastavit tak, aby se daly tisknout jenom v určeném časovém intervalu.  
  
 Třídy <xref:System.Printing.PrintQueue> a<xref:System.Printing.PrintSystemJobInfo> zveřejněné v rozhraní API Microsoft .NET Framework poskytují prostředky pro vzdálenou kontrolu toho, zda může daná tisková úloha tisknout v dané frontě v aktuálním čase.  
  
## <a name="example"></a>Příklad  
 Příkladem níže je ukázka, která může diagnostikovat problémy s tiskovou úlohou.  
  
 Existují dva hlavní kroky pro tento druh funkce, jak je znázorněno níže.  
  
1. Přečtěte si <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> vlastnosti <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> <xref:System.Printing.PrintQueue> a a určete, zda je mezi nimi aktuální čas.  
  
2. Přečtěte si <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> vlastnosti <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> <xref:System.Printing.PrintSystemJobInfo> a a určete, zda je mezi nimi aktuální čas.  
  
 Ale komplikace se projeví z faktu, že <xref:System.DateTime> tyto vlastnosti nejsou objekty. Místo toho jsou <xref:System.Int32> objekty, které vyjadřují denní dobu jako počet minut od půlnoci. Kromě toho se nejedná o půlnoc v aktuálním časovém pásmu, ale o půlnoci UTC (koordinovaný světový čas).  
  
 První příklad kódu představuje statickou metodu **ReportQueueAndJobAvailability**, která je předána <xref:System.Printing.PrintSystemJobInfo> a volá pomocné metody k určení, zda se může úloha tisknout v aktuálním čase a v případě, že je může tisknout. Všimněte si, <xref:System.Printing.PrintQueue> že metoda není předána metodě. Důvodem je, <xref:System.Printing.PrintSystemJobInfo> že zahrnuje odkaz na frontu ve své <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> vlastnosti.  
  
 Podřízené metody zahrnují přetíženou metodu **ReportAvailabilityAtThisTime** , která může použít buď <xref:System.Printing.PrintQueue> nebo <xref:System.Printing.PrintSystemJobInfo> jako parametr. K dispozici je také **TimeConverter. ConvertToLocalHumanReadableTime**. Všechny tyto metody jsou popsány níže.  
  
 Metoda **ReportQueueAndJobAvailability** se spustí tak, že zkontroluje, jestli není v tuto chvíli fronta nebo tisková úloha dostupná. Pokud je některá z nich nedostupná, zkontroluje, jestli není fronta k dispozici. Pokud není k dispozici, pak metoda oznámí tuto skutečnost a čas, kdy bude fronta opět k dispozici. Pak zkontroluje úlohu a pokud není k dispozici, ohlásí příští časové období, kdy může tisknout. Nakonec metoda oznamuje Nejdřívější čas, kdy může úloha tisknout. To je pozdější, než dvakrát.  
  
- Čas, kdy bude tisková fronta příště dostupná.  
  
- Čas, kdy bude tisková úloha příště k dispozici.  
  
 Při vykazování času dne <xref:System.DateTime.ToShortTimeString%2A> je metoda volána také proto, že tato metoda potlačuje roky, měsíce a dny z výstupu. Nemůžete omezit dostupnost tiskové fronty ani tiskové úlohy na konkrétní roky, měsíce nebo dny.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Dvě přetížení metody **ReportAvailabilityAtThisTime** jsou identická s výjimkou typu, který je předaný, takže níže je uvedena pouze <xref:System.Printing.PrintQueue> verze.  
  
> [!NOTE]
> Skutečnost, že metody jsou identické s výjimkou typu, vyvolává otázku proč ukázka nevytvoří obecnou metodu **\<ReportAvailabilityAtThisTime T >** . Důvodem je, že taková metoda by musela být omezena na třídu, která má vlastnosti **StartTimeOfDay** a **UntilTimeOfDay** , kterou metoda volá, ale obecnou metodu lze omezit pouze na jedinou třídu a jedinou třídou, která je společná pro obě. <xref:System.Printing.PrintQueue> a ve<xref:System.Printing.PrintSystemJobInfo>stromové struktuře dědičnosti<xref:System.Printing.PrintSystemObject> nemá takové vlastnosti.  
  
 Metoda **ReportAvailabilityAtThisTime** (uvedená v následujícím příkladu kódu) začíná inicializací <xref:System.Boolean> proměnné Sentinel na. `true` V případě `false`, že fronta není k dispozici, bude obnovena.  
  
 Dále metoda zkontroluje, zda jsou časy Start a "do" stejné. Pokud jsou, fronta je vždy k dispozici, takže se metoda vrátí `true`.  
  
 Pokud není fronta k dispozici po celou dobu, metoda použije statickou <xref:System.DateTime.UtcNow%2A> vlastnost k získání aktuálního času <xref:System.DateTime> jako objektu. (Nepotřebujeme místní čas, protože <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> vlastnosti a <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> jsou samy v čase UTC.)  
  
 Tyto dvě vlastnosti <xref:System.DateTime> však nejsou objekty. Jsou <xref:System.Int32>v čase vyjádřené jako počet minut po UTC-půlnoci. Proto musíme převést náš <xref:System.DateTime> objekt na minuty po půlnoci. V takovém případě metoda jednoduše zkontroluje, jestli je "Now" mezi dobou spuštění fronty a "do", nastaví Sentinel na hodnotu false, pokud "Now" není mezi dvěma časy a vrátí Sentinel.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 Metoda **TimeConverter. ConvertToLocalHumanReadableTime** (uvedená v následujícím příkladu kódu) nepoužívá žádné metody, které jsou zavedeny v rámci Microsoft .NET Framework, takže diskuze je stručná. Metoda má úlohu s dvojitou konverzí: musí přijmout celé číslo vyjadřující minuty po půlnoci a převést ji na čas, který je čitelný člověkem, a musí to převést na místní čas. To to provede tím, že nejprve vytvoří <xref:System.DateTime> objekt, který je nastaven na půlnoc UTC, a pak <xref:System.DateTime.AddMinutes%2A> použije metodu k přidání minut, které byly předány metodě. To vrací nové <xref:System.DateTime> vyjádření původního času, který byl předán metodě. <xref:System.DateTime.ToLocalTime%2A> Metoda pak tuto metodu převede na místní čas.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
