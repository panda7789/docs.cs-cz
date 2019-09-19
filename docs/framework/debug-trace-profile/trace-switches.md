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
ms.openlocfilehash: b796d79fc6acf7d54aac7c69d376e587144d14d1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052264"
---
# <a name="trace-switches"></a>Přepínače trasování
Přepínače trasování umožňují povolit, zakázat a filtrovat výstup trasování. Jsou to objekty, které existují ve vašem kódu a lze je nakonfigurovat externě prostřednictvím souboru. config. Existují tři typy přepínačů trasování, které jsou k dispozici v <xref:System.Diagnostics.BooleanSwitch> .NET Framework: třídy <xref:System.Diagnostics.TraceSwitch> , třídy a <xref:System.Diagnostics.SourceSwitch> třídy. <xref:System.Diagnostics.BooleanSwitch> Třída funguje jako přepínač Switch, buď povolení nebo zákaz řady příkazů trasování. <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.TraceSource> Třídy <xref:System.Diagnostics.TraceSwitch> a <xref:System.Diagnostics.SourceSwitch> umožňují povolit přepínač trasování pro konkrétní úroveň trasování, aby se zobrazily zprávy nebo zprávy zadané pro tuto úroveň a všechny úrovně pod ní. Pokud přepínač zakážete, zprávy trasování se nezobrazí. Všechny tyto třídy jsou odvozeny z **přepínače**třídy abstract (**MustInherit**), stejně jako všechny uživatelsky vyvíjené přepínače.  
  
 Přepínače trasování mohou být užitečné pro filtrování informací. Můžete například chtít zobrazit každou zprávu trasování v modulu Data Access, ale pouze chybové zprávy ve zbývající části aplikace. V takovém případě byste použili jeden přepínač trasování pro modul Data Access a jeden přepínač pro zbytek aplikace. Když použijete soubor. config ke konfiguraci přepínačů na příslušná nastavení, můžete určit, jaké typy trasovacích zpráv jste dostali. Další informace najdete v tématu [jak: Vytváření, inicializace a konfigurace přepínačů](how-to-create-initialize-and-configure-trace-switches.md)trasování.  
  
 Obvykle je nasazená aplikace spouštěna s vypnutými přepínači, aby uživatelé nemuseli sledovat spoustu nepodstatných trasovacích zpráv, které se zobrazují na obrazovce, nebo naplňovat soubor protokolu při spuštění aplikace. Pokud při provádění aplikace dojde k problému, můžete aplikaci zastavit, povolit přepínače a restartovat aplikaci. Pak se zobrazí trasovací zprávy.  
  
 Chcete-li použít přepínač, musíte nejprve vytvořit objekt Switch z třídy **BooleanSwitch** , třídy **TraceSwitch** nebo třídy přepínače definované vývojářem. Další informace o vytváření přepínačů definovaných pro vývojáře naleznete v tématu <xref:System.Diagnostics.Switch> třída v referenci .NET Framework. Pak nastavíte hodnotu konfigurace, která určuje, kdy má být objekt Switch použit. Pak otestujete nastavení objektu Switch v různých metodách trasování (nebo **ladění** **) trasování.**  
  
## <a name="trace-levels"></a>Úrovně trasování  
 Při použití **TraceSwitch**existují další okolnosti. Objekt **TraceSwitch** má čtyři vlastnosti, které vracejí **logické** hodnoty, což znamená, zda je přepínač nastaven alespoň na konkrétní úroveň:  
  
- <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Úrovně vám umožňují omezit množství trasovacích informací, které obdržíte, jenom k informacím potřebným k vyřešení problému. Úroveň podrobností, kterou požadujete ve výstupu trasování, určíte nastavením a konfigurací přepínačů trasování na příslušnou úroveň trasování. Můžete dostávat chybové zprávy, varovné zprávy, informativní zprávy, podrobné trasovací zprávy nebo žádná zpráva vůbec.  
  
 Je zcela na vás, abyste se rozhodli, jaký druh zprávy přidružit k jednotlivým úrovním. Obsah trasovacích zpráv obvykle závisí na tom, co přiřadíte k jednotlivým úrovním, ale určíte rozdíly mezi úrovněmi. Je možné, že budete chtít poskytnout podrobné popisy problému na úrovni 3 (**informace**), například poskytnout pouze referenční číslo chyby na úrovni 1 (**Chyba**). Je zcela na vás, abyste se rozhodli, jaké schéma funguje nejlépe ve vaší aplikaci.  
  
 Tyto vlastnosti odpovídají hodnotám 1 až 4 výčtu **TraceLevel** . Následující tabulka uvádí úrovně výčtu **TraceLevel** a jejich hodnoty.  
  
|Výčtová hodnota|Celočíselná hodnota|Typ zobrazené zprávy (nebo zápis do zadaného cíle výstupu)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Off|0|Žádné|  
|Chyba|1|Pouze chybové zprávy|  
|Upozornění|2|Varovné zprávy a chybové zprávy|  
|Informace o|3|Informační zprávy, varovné zprávy a chybové zprávy|  
|Podrobnosti|4|Podrobné zprávy, informativní zprávy, varovné zprávy a chybové zprávy|  
  
 Vlastnosti **TraceSwitch** označují maximální úroveň trasování pro přepínač. To znamená, že trasovací informace jsou zapsány pro zadanou úroveň i pro všechny nižší úrovně. Například pokud má **TraceInfo** **hodnotu true**, pak **zaznamenáno: TraceError** a **zaznamenáno: TraceWarning** jsou také **true** , ale **TraceVerbose** může být **nepravdivá**.  
  
 Tyto vlastnosti jsou jen pro čtení. Objekt **TraceSwitch** je automaticky nastaví, když je nastavena vlastnost **TraceLevel** . Příklad:  
  
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
 Kromě poskytování **BooleanSwitch** a **TraceSwitch**můžete definovat vlastní přepínače děděním z třídy **Switch** a přepsáním metod základní třídy pomocí přizpůsobených metod. Další informace o vytváření přepínačů definovaných pro vývojáře naleznete v tématu <xref:System.Diagnostics.Switch> třída v referenci .NET Framework.  
  
## <a name="see-also"></a>Viz také:

- [Moduly naslouchání trasování](trace-listeners.md)
- [Postupy: Přidání příkazů trasování do kódu aplikace](how-to-add-trace-statements-to-application-code.md)
- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
