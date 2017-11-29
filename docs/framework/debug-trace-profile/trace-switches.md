---
title: "Přepínače trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 082d84fe0ac4193f3da5ac9be52789432bde76aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="trace-switches"></a>Přepínače trasování
Trasování – přepínače umožňují povolit, zakázat a filtrovat výstup trasování. Jsou objekty, které existují ve vašem kódu a možné externě nakonfigurovat pomocí souboru .config. Existují tři typy trasování – přepínače zadaný v rozhraní .NET Framework: <xref:System.Diagnostics.BooleanSwitch> třídy, <xref:System.Diagnostics.TraceSwitch> třída a <xref:System.Diagnostics.SourceSwitch> třídy. <xref:System.Diagnostics.BooleanSwitch> Třída slouží jako přepínač přepnutí, povolení nebo zakázání celou řadu příkazů trasování. <xref:System.Diagnostics.TraceSwitch> a <xref:System.Diagnostics.SourceSwitch> třídy možné povolit přepínače trasování pro konkrétní trasování úroveň tak, aby <xref:System.Diagnostics.Trace> nebo <xref:System.Diagnostics.TraceSource> zadané pro tuto úroveň a nižší úrovně všechny zprávy se zobrazují. Pokud zakážete přepínač, nebude se zobrazovat trasovací zprávy. Všechny tyto třídy jsou odvozeny od abstraktní (**MustInherit**) třídy **přepínač**, jako by všechny uživatele vyvinuté přepínače.  
  
 Trasování – přepínače může být užitečná pro filtrování informací. Například můžete chtít zobrazit všechny zprávy trasování v modulu přístupu k datům, ale pouze chybové zprávy ve zbývající části aplikace. V takovém případě byste použili přepínače jeden trasování pro modulu přístupu k datům a jeden pro zbývající aplikace. Pomocí souboru .config nakonfigurovat přepínače na příslušná nastavení může řídit, jaké typy zpráva trasování, která se vám zobrazila. Další informace najdete v tématu [postupy: vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md).  
  
 Obvykle je nasazené aplikace provést s jeho přepínače zakázaná, tak, aby uživatelé nemusí sledovat mnoho důležité trasování zpráv zobrazovaných na obrazovce nebo naplňování soubor protokolu jako spouštět aplikace. Pokud k problému dojde během provádění aplikací, zastavte aplikaci a povolit přepínačů restartování aplikace. Potom zobrazí trasování zpráv.  
  
 Chcete-li použít přepínač musíte nejdřív vytvořit objekt přepínač z **BooleanSwitch** třída, **TraceSwitch** , nebo třída definované vývojáře přepínače. Další informace o vytváření definované vývojáře přepínačů najdete v tématu <xref:System.Diagnostics.Switch> třídy v odkazu rozhraní .NET Framework. Pak můžete nastavit hodnotu konfigurace, která určuje, když je objekt v přepínač, který se má použít. Potom otestovat nastavení přepínače objektu v různých **trasování** (nebo **ladění**) metody trasování.  
  
## <a name="trace-levels"></a>Úrovně trasování  
 Při použití **TraceSwitch**, existují další aspekty. A **TraceSwitch** objekt má čtyři vlastnosti, které vracejí **Boolean** hodnoty, která určuje, jestli je přepínač nastaven alespoň na konkrétní úroveň:  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceError%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceWarning%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceInfo%2A?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceSwitch.TraceVerbose%2A?displayProperty=nameWithType>  
  
 Úrovně umožňují omezit množství informací o trasování, abyste ji pouze tyto informace, které jsou potřebné k vyřešení problému. Můžete zadat úroveň podrobností, které chcete ve výstupu trasování nastavení a konfigurace přepínačů trasování na úroveň odpovídající trasování. Chybové zprávy, zprávy upozornění, informační zprávy, podrobného trasování zprávy nebo žádná zpráva může vůbec přijímat.  
  
 Je zcela na vás se rozhodnout, jaký druh zpráva pro přidružení k každou úroveň. Obvykle obsah trasování zprávy závisí na přidružit jednotlivé úrovně, ale určit rozdíly mezi úrovněmi. Můžete chtít Zadejte podrobný popis problému na úrovni 3 (**informace**), například, ale pouze referenční číslo chyby na úrovni 1 (**chyba**). Je zcela na vás nechá rozhodnout, jaké schéma funguje nejlépe ve vaší aplikaci.  
  
 Tyto vlastnosti odpovídají hodnot 1 až 4 **TraceLevel** výčtu. Následující tabulka uvádí seznam úrovní **TraceLevel** výčet a jejich hodnoty.  
  
|Výčtová hodnota|Celočíselná hodnota|Typ zprávy zobrazit (nebo zapisovat do zadané výstupní cíl)|  
|----------------------|-------------------|---------------------------------------------------------------------------|  
|Off|0|Žádné|  
|Chyba|1|Pouze chybové zprávy|  
|Upozornění|2|Zprávy upozornění a chybové zprávy|  
|Informace o|3|Informační zprávy, upozornění a chybové zprávy|  
|Verbose|4|Podrobné zprávy, informační zprávy, upozornění a chybové zprávy|  
  
 **TraceSwitch** vlastnosti určují úroveň maximální trasování pro přepínač. To znamená informace o trasování je napsán pro úroveň zadán stejně jako u všech nižších úrovních. Například pokud **TraceInfo** je **true**, pak **TraceError** a **trasování** jsou také **true** ale **TraceVerbose** dobře může být **false**.  
  
 Tyto vlastnosti jsou jen pro čtení. **TraceSwitch** objekt automaticky nastaví při **TraceLevel** je nastavena. Příklad:  
  
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
  
## <a name="developer-defined-switches"></a>Definované vývojáře přepínače  
 Kromě **BooleanSwitch** a **TraceSwitch**, můžete definovat vlastní přepínače dědění ze **přepínač** třídy a přepsáním metody třídy base s vlastní metody. Další informace o vytváření definované vývojáře přepínačů najdete v tématu <xref:System.Diagnostics.Switch> třídy v odkazu rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 [Trasování – moduly naslouchání](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
