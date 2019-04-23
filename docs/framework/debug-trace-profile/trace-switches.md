---
title: Přepínače trasování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], trace switches
- trace switches, about trace switches
- tracing [.NET Framework], level of detail
- switches, trace
- trace switches
- trace switches, creating custom
ms.assetid: 8ab913aa-f400-4406-9436-f45bc6e54fbe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85a1a017197826717280f53995ed98f26f1d80bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132662"
---
# <a name="trace-switches"></a>Přepínače trasování
Přepínače trasování umožňují povolit, zakázat a filtrovat výstup trasování. Jsou objekty, které existují ve vašem kódu a je možné nakonfigurovat externě pomocí souboru .config. Existují tři typy přepínačů trasování, které jsou k dispozici v rozhraní .NET Framework: <xref:System.Diagnostics.BooleanSwitch> třídy, <xref:System.Diagnostics.TraceSwitch> třídy a <xref:System.Diagnostics.SourceSwitch> třídy. <xref:System.Diagnostics.BooleanSwitch> Třída slouží jako přepínač, povolení nebo zakázání různých příkazů trasování. <xref:System.Diagnostics.TraceSwitch> a <xref:System.Diagnostics.SourceSwitch> tříd bylo možné povolit přepínač trasování pro trasování konkrétní úroveň tak, aby <xref:System.Diagnostics.Trace> nebo <xref:System.Diagnostics.TraceSource> zobrazí zprávy zadané pro tuto úroveň a všechny úrovně pod ním. Pokud zakážete přepínač, zprávy trasování se nezobrazí. Všechny tyto třídy jsou odvozeny od abstraktní (**MustInherit**) třídy **přepínač**, jako by všechny přepínače vyvinutou v Unity uživatele.  
  
 Přepínače trasování může být užitečné pro filtrování informací. Například můžete chtít zobrazit všechny zprávy trasování v modulu přístupu k datům, ale pouze chybové zprávy ve zbývající části aplikace. V takovém případě můžete využít jeden trasování přepínače pro modulu přístupu k datům a jeden pro ostatní aplikace. Pomocí souboru .config konfigurace přepínače, které příslušná nastavení může řídit, jaké typy trasování zpráv, jste obdrželi. Další informace najdete v tématu [jak: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Obvykle s jeho přepínači zakázána, je proveden nasazenou aplikaci tak, aby uživatelé nemusí dodržovat spoustu irelevantní trasování zprávy uvedené na obrazovce nebo nezaplňuje soubor protokolu za běhu aplikace. Pokud k problému dochází při spuštění aplikace, zastavte aplikaci a povolit přepínače restartování aplikace. Pak se zobrazí trasovací zprávy.  
  
 Chcete-li použít přepínač musíte nejdřív vytvořit objekt přepínače z **BooleanSwitch** třídy, **TraceSwitch** třídu nebo třídu přepínač definovaný pro vývojáře. Další informace o vytváření definované pro vývojáře přepínače najdete v článku <xref:System.Diagnostics.Switch> třídy v referenční dokumentaci rozhraní .NET Framework. Nastavit hodnotu konfigurace, která určuje, kdy objekt přepínače má být použit. Potom otestovat nastavení přepínače objektu v různých **trasování** (nebo **ladění**) metody trasování.  
  
## <a name="trace-levels"></a>Úrovně trasování  
 Při použití **TraceSwitch**, existují ještě další důležité okolnosti. A **TraceSwitch** objekt má čtyři vlastnosti, které vracejí **logická** hodnoty určující, jestli přepínač nastavený na alespoň určitou úroveň:  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Úrovně umožňují omezit množství informací o trasování, který jste dostali k pouze těmto informacím, které jsou potřebné k vyřešení problému. Můžete zadat úroveň podrobností, které chcete výstup trasování tak, že nastavení a konfigurace přepínačů trasování pro příslušnou úroveň. Chybové zprávy, upozornění, informační zprávy, podrobného trasování zprávy nebo žádná zpráva může vůbec přijímat.  
  
 Je zcela v kompetenci můžete určit, jaký druh zpráva pro přidružení k každé úrovni. Obvykle obsah trasování zpráv, které závisí na přidružit každou úroveň, ale zjistit rozdíly mezi úrovněmi. Můžete chtít poskytnout podrobný popis problému na úrovni 3 (**informace**), například ale poskytnout jenom referenční číslo chyby na úrovni 1 (**chyba**). Je zcela v kompetenci můžete určit, jaké schéma funguje nejlépe ve vaší aplikaci.  
  
 Tyto vlastnosti odpovídají hodnoty 1 až 4 **TraceLevel** výčtu. Následující tabulka uvádí, které **TraceLevel** výčet a jejich hodnoty.  
  
|Výčtová hodnota|Celočíselná hodnota|Typ zprávy zobrazí (nebo zapsat do zadaného výstupního cíle)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Off|0|Žádné|  
|Chyba|1|Pouze chybové zprávy|  
|Upozornění|2|Zprávy upozornění a chybové zprávy|  
|Informace o|3|Informační zprávy, upozornění a chybové zprávy|  
|Podrobnosti|4|Podrobné zprávy, informační zprávy, upozornění a chybové zprávy|  
  
 **TraceSwitch** vlastnosti určují maximální úroveň pro přepínač. To znamená se zapíšou informace trasování zadaný stejně jako u všech úrovní nižší úrovně. Například pokud **TraceInfo** je **true**, pak **TraceError** a **trasování** jsou také **true** ale **TraceVerbose** nejde **false**.  
  
 Tyto vlastnosti jsou jen pro čtení. **TraceSwitch** objekt je automaticky nastaví při **TraceLevel** je nastavena. Příklad:  
  
```vb  
Dim myTraceSwitch As New TraceSwitch("SwitchOne", "The first switch")  
myTraceSwitch.Level = TraceLevel.Info  
' This message box displays true, because setting the level to  
' TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString())  
' This messagebox displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString())  
```  
  
```csharp  
System.Diagnostics.TraceSwitch myTraceSwitch =   
   new System.Diagnostics.TraceSwitch("SwitchOne", "The first switch");  
myTraceSwitch.Level = System.Diagnostics.TraceLevel.Info;  
// This message box displays true, because setting the level to   
// TraceLevel.Info sets all lower levels to true as well.  
MessageBox.Show(myTraceSwitch.TraceWarning.ToString());  
// This message box displays false.  
MessageBox.Show(myTraceSwitch.TraceVerbose.ToString());  
```  
  
## <a name="developer-defined-switches"></a>Přepínače definované pro vývojáře  
 Kromě toho, že **BooleanSwitch** a **TraceSwitch**, můžete definovat vlastní přepínače děděním z **přepínač** třídy a přepsáním metody třídy base pomocí vlastní metody. Další informace o vytváření definované pro vývojáře přepínače najdete v článku <xref:System.Diagnostics.Switch> třídy v referenční dokumentaci rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také:

- [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
