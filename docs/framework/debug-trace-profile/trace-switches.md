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
ms.openlocfilehash: a8ce4ee5de4d330b88e98e85cce4b6547e969613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181722"
---
# <a name="trace-switches"></a>Přepínače trasování
Přepínače trasování umožňují povolit, zakázat a filtrovat výstup trasování. Jedná se o objekty, které existují ve vašem kódu a mohou být nakonfigurovány externě prostřednictvím souboru .config. Existují tři typy trasovací přepínače k dispozici <xref:System.Diagnostics.BooleanSwitch> v rozhraní <xref:System.Diagnostics.TraceSwitch> .NET <xref:System.Diagnostics.SourceSwitch> Framework: třída, třída a třída. Třída <xref:System.Diagnostics.BooleanSwitch> funguje jako přepínač, povolení nebo zakázání různých příkazů trasování. <xref:System.Diagnostics.TraceSwitch> Třídy <xref:System.Diagnostics.SourceSwitch> a umožňují povolit přepínač trasování pro určitou <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.TraceSource> úroveň trasování tak, aby se zobrazily zprávy nebo zadané pro tuto úroveň a všechny úrovně pod ní. Pokud přepínač zakážete, trasovací zprávy se nezobrazí. Všechny tyto třídy jsou odvozeny z abstraktní (**MustInherit**) třídy **Switch**, stejně jako všechny přepínače vyvinuté uživatelem.  
  
 Přepínače trasování mohou být užitečné pro filtrování informací. Můžete například chtít zobrazit každou zprávu trasování v modulu pro přístup k datům, ale pouze chybové zprávy ve zbytku aplikace. V takovém případě byste použili jeden přepínač trasování pro modul přístupu k datům a jeden přepínač pro zbytek aplikace. Pomocí souboru .config ke konfiguraci přepínačů na příslušná nastavení můžete určit, jaké typy přijatých trasovacích zpráv jste obdrželi. Další informace naleznete v [tématu How to: Create, Initialize and Configure Trace Switches](how-to-create-initialize-and-configure-trace-switches.md).  
  
 Nasazené aplikace je obvykle spuštěna se zakázanými přepínači, takže uživatelé nemusí sledovat mnoho irelevantních trasovacích zpráv, které se zobrazují na obrazovce nebo vyplňují soubor protokolu při spuštění aplikace. Pokud během spuštění aplikace vznikne problém, můžete aplikaci zastavit, povolit přepínače a aplikaci restartovat. Poté se zobrazí trasovací zprávy.  
  
 Chcete-li použít přepínač, musíte nejprve vytvořit objekt přepínače z třídy **BooleanSwitch,** třídy **TraceSwitch** nebo třídy přepínače definované vývojářem. Další informace o vytváření přepínačů definovaných vývojářem naleznete v <xref:System.Diagnostics.Switch> části Třída v odkazu rozhraní .NET Framework. Potom nastavíte hodnotu konfigurace, která určuje, kdy má být použit objekt přepínače. Potom otestovat nastavení switch objektu v různých **trasování** (nebo **ladění)** trasování metody.  
  
## <a name="trace-levels"></a>Úrovně trasování  
 Při použití **TraceSwitch**, existují další důležité informace. Objekt **TraceSwitch** má čtyři vlastnosti, které vracejí **logické** hodnoty označující, zda je přepínač nastaven alespoň na určitou úroveň:  
  
- <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Úrovně umožňují omezit množství informací o trasování, které obdržíte, pouze na informace potřebné k vyřešení problému. Požadovanou úroveň podrobností ve výstupu trasování určíte nastavením a konfigurací přepínačů trasování na příslušnou úroveň trasování. Můžete přijímat chybové zprávy, varovné zprávy, informační zprávy, podrobné trasovací zprávy nebo vůbec žádnou zprávu.  
  
 Je zcela na vás, rozhodnout, jaký druh zprávy spojit s každou úroveň. Obsah trasovacích zpráv obvykle závisí na tom, co přidružíte ke každé úrovni, ale určíte rozdíly mezi úrovněmi. Můžete například zadat podrobný popis problému na úrovni 3 (**Informace),** ale zadat pouze referenční číslo chyby na úrovni 1 (**Chyba**). Je zcela na vás, rozhodnout, jaké schéma funguje nejlépe ve vaší žádosti.  
  
 Tyto vlastnosti odpovídají hodnotám 1 až 4 výčtu **TraceLevel.** V následující tabulce jsou uvedeny úrovně výčtu **TraceLevel** a jejich hodnoty.  
  
|Výčet|Celočíselná hodnota|Typ zobrazené zprávy (nebo zapsané do zadaného výstupního cíle)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Vypnuto|0|Žádný|  
|Chyba|1|Pouze chybové zprávy|  
|Upozornění|2|Varovné a chybové zprávy|  
|Informace|3|Informační zprávy, varovné zprávy a chybové zprávy|  
|Verbose|4|Podrobné zprávy, informační zprávy, varovné zprávy a chybové zprávy|  
  
 Vlastnosti **TraceSwitch** označují maximální úroveň trasování přepínače. To znamená, že trasování informace je zapsána pro zadanou úroveň, stejně jako pro všechny nižší úrovně. Například pokud **TraceInfo** je **true**, pak **TraceError** a **TraceWarning** jsou také **true,** ale **TraceVerbose** může být **false**.  
  
 Tyto vlastnosti jsou jen pro čtení. **TraceSwitch** objekt automaticky nastaví je, když **traceLevel** vlastnost je nastavena. Například:  
  
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
  
## <a name="developer-defined-switches"></a>Přepínače definované vývojářem  
 Kromě poskytování **BooleanSwitch** a **TraceSwitch**, můžete definovat vlastní přepínače děděním z **Switch** třídy a přepsání metody základní třídy s vlastní metody. Další informace o vytváření přepínačů definovaných vývojářem naleznete v <xref:System.Diagnostics.Switch> části Třída v odkazu rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také

- [Moduly naslouchání trasování](trace-listeners.md)
- [Postupy: Přidání příkazů trasování do kódu aplikace](how-to-add-trace-statements-to-application-code.md)
- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
