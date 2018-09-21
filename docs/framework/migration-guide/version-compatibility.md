---
title: Kompatibilita verzí v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d3d0e2dbd57d9581d1c8b0ca42d1e9d556d8905
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46528850"
---
# <a name="version-compatibility-in-the-net-framework"></a>Kompatibilita verzí v rozhraní .NET Framework
Zpětná kompatibilita znamená, že aplikace vyvinutá pro konkrétní verzi platformy poběží v novějších verzích této platformy. Rozhraní .NET Framework se snaží maximalizovat zpětnou kompatibilitu: zdrojový kód napsaný pro jednu verzi rozhraní .NET Framework by měl kompilovat v novějších verzích rozhraní .NET Framework a binární soubory, které běží na jednu verzi rozhraní .NET Framework by se měly chovat identicky v novější verze rozhraní .NET Framework.  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>Kompatibilita verzí pro aplikace  
 Ve výchozím nastavení je aplikace spuštěna ve verzi rozhraní .NET Framework, pro kterou byla vytvořena. Pokud tato verze není k dispozici a konfigurační soubor aplikace nedefinuje podporované verze, může dojít k chybě inicializace rozhraní .NET Framework. V takovém případě se nezdaří pokus o spuštění aplikace.  
  
 Chcete-li definovat konkrétní verze, na kterých běží vaše aplikace, přidejte jeden nebo více [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) prvky do konfiguračního souboru aplikace. Každý `<supportedRuntime>` element uvádí podporovanou verzi modulu runtime, přičemž první zadání nejvíce upřednostňovanou verzi a poslední zadání pak nejméně preferovanou verzi.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 Další informace najdete v tématu [postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).  
  
## <a name="version-compatibility-for-components"></a>Kompatibilita verzí pro komponenty  
 Aplikace může kontrolovat verzi rozhraní .NET Framework, na kterém běží, ale součást nikoli. Komponenty a knihovny tříd jsou načteny v kontextu konkrétní aplikace a proto se automaticky spouštějí ve verzi rozhraní .NET Framework, na které aplikace poběží.  
  
 Z důvodu tohoto omezení je pro součásti obzvlášť důležité zajištění kompatibility. Od verze rozhraní .NET Framework 4, můžete zadat míru, do jaké se očekává součást zůstane kompatibilní ve více verzích použitím <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> atributu pro tuto součást. Nástroje pro tento atribut slouží ke zjištění, že případné porušení kompatibilitu zaručit v budoucích verzích komponenty.  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>Zpětná kompatibilita a rozhraní .NET Framework 4.5  
 Rozhraní .NET Framework 4.5 a novější verze jsou zpětně kompatibilní s aplikacemi, které byly vytvořeny v dřívějších verzích rozhraní .NET Framework. Jinými slovy aplikace a komponenty sestavené v předchozích verzích budou fungovat bez úprav na rozhraní .NET Framework 4.5 a novější verze. Ale ve výchozím nastavení, aplikace spuštěny ve verzi modulu common language runtime pro kterou byly vyvinuty, tak může být zapotřebí poskytnout konfigurační soubor aplikace spustit na .NET Framework 4.5 nebo novější verze. Další informace najdete v tématu [Kompatibilita verzí pro aplikace](#Apps) dříve v tomto článku.  
  
 V praxi však může být tato kompatibilita porušena zdánlivě bezvýznamnými změnami v rozhraní .NET Framework a změnami v programovacích postupech. Vylepšení výkonu v rozhraní .NET Framework 4.5 můžete například odhalit spor, který nedošlo k v dřívějších verzích. Podobně použití pevně zakódované cesty k sestavením .NET Framework, provádění porovnání rovnosti s konkrétní verzí rozhraní .NET Framework a získání hodnoty soukromého pole pomocí reflexe nejsou zpětně kompatibilní postupy. Kromě toho zahrnuje každá verze rozhraní .NET Framework opravy chyb a změny související se zabezpečením, které mohou ovlivnit kompatibilitu některých aplikací a komponent.  
  
 Pokud vaše aplikace nebo komponenta nefunguje podle očekávání v rozhraní .NET Framework 4.5 (včetně jeho vydání bodu [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2, použijte následující kontrolní seznamy:  
  
-  Pokud vaše aplikace byla vyvinuta v jakékoli verzi rozhraní .NET Framework počínaje .NET Framework 4.0 naleznete v tématu [kompatibilita aplikací v rozhraní .NET Framework](application-compatibility.md) pro vygenerování seznamu změn mezi vaší cílovou verzi rozhraní .NET Framework a verze, na kterém je spuštěná aplikace.  

- Pokud budete mít aplikaci .NET Framework 3.5, viz také informace [problémy s migrací rozhraní .NET Framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md).

- Pokud budete mít aplikaci .NET Framework 2.0, viz také informace [změny v rozhraní .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkId=186989).

- Pokud budete mít aplikaci .NET Framework 1.1, viz také informace [změny v rozhraní .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkID=125263).  
  
-   Pokud znovu kompilujete existující zdrojový kód pro spuštění v rozhraní .NET Framework 4.5 nebo jeho verze, nebo pokud vyvíjíte novou verzi aplikace nebo komponenty, která se zaměřuje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeho verze z existující základní, kontrola zdrojového kódu [ What's Obsolete in knihovny tříd](../../../docs/framework/whats-new/whats-obsolete.md) pro zastaralých typech a členech a použijte popsané řešení. (Dříve zkompilovaný kód bude nadále spouštět proti typům a členům, které jsou označené jako zastaralé.)  
  
-   Pokud zjistíte, že změna [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] způsobila poškození vaší aplikace, [schéma nastavení běhového prostředí](../../../docs/framework/configure-apps/file-schema/runtime/index.md) k určení, zda můžete použít nastavení modulu runtime v konfiguračním souboru aplikace k obnovení předchozího chování.  
  
-   Pokud narazíte na problém, který nebyl zdokumentován, otevřete problém na [web komunity vývojářů pro .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) nebo otevřete problém [úložiště GitHub Microsoft/dotnet](https://github.com/microsoft/dotnet/issues).
  
## <a name="compatibility-and-side-by-side-execution"></a>Spuštění kompatibility a vedle sebe  
 Pokud nemůžete najít vhodné řešení problému, nezapomeňte, že pracuje s verzemi 1.1, 2.0 a 3.5 rozhraní .NET Framework 4.5 (nebo některá z jeho vydání bodu) a je místní aktualizace, která nahrazuje verzi 4. U aplikací s cílovou verzí 1.1, 2.0 a 3.5 můžete nainstalovat odpovídající verzi rozhraní .NET Framework na cílovém počítači spusťte aplikaci v tom nejlepším prostředí. Další informace o spuštění vedle sebe, naleznete v tématu [spuštění vedle sebe](../../../docs/framework/deployment/side-by-side-execution.md).  
  
## <a name="see-also"></a>Viz také  
 [Co je nového](../../../docs/framework/whats-new/index.md)  
 [Zastaralé položky v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Kompatibilita aplikací](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Zásady životního cyklu podpory rozhraní Microsoft .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=248212)  
 [Potíže s migrací rozhraní .NET framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)
