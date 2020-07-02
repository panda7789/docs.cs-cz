---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614524"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase nešíří výjimky OnStart.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,7 a dřívějších verzích nejsou výjimky vyvolané při spuštění služby šířeny volajícímu <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> .<br/>Počínaje aplikacemi, které cílí na .NET Framework 4.7.1, modul runtime šíří výjimky pro <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> služby, které se nedaří spustit.

#### <a name="suggestion"></a>Návrh

Při spuštění služby, pokud dojde k výjimce, bude tato výjimka šířena. To by mělo pomáhat diagnostikovat případy, kdy se služby nedaří spustit. <br/>Pokud je toto chování nežádoucí, můžete si ho odhlásit přidáním následujícího &lt; &gt; elementu AppContextSwitchOverrides do &lt; &gt; oddílu runtime konfiguračního souboru aplikace:

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

Pokud je vaše aplikace cílena na starší verzi než 4.7.1, ale chcete mít toto chování, přidejte následující &lt; &gt; element AppContextSwitchOverrides do &lt; oddílu runtime &gt; konfiguračního souboru aplikace:

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
