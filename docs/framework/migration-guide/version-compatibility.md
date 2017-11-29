---
title: "Kompatibilita verzí v rozhraní .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 166d61339d2b74f378b50ade4b78fd41e9692f76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="version-compatibility-in-the-net-framework"></a>Kompatibilita verzí v rozhraní .NET Framework
Zpětná kompatibilita znamená, že aplikaci, která byla vyvinuta pro konkrétní verze platformy bude spuštěna v novějších verzích této platformě. Rozhraní .NET Framework snaží co zpětné kompatibility: zdrojový kód napsaný pro jednu verzi rozhraní .NET Framework by měl kompilovat v novějších verzích rozhraní .NET Framework a binární soubory, které běží na jednu verzi rozhraní .NET Framework se měl chovat stejně jako na novější verze rozhraní .NET Framework.  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>Kompatibilita verzí pro aplikace  
 Ve výchozím nastavení se aplikace spustí na verzi rozhraní .NET Framework, který byl vytvořen pro. Pokud tuto verzi není k dispozici a konfiguračního souboru aplikace nedefinuje podporované verze, může dojít k chybě inicializace rozhraní .NET Framework. V takovém případě se nezdaří pokus o spuštění aplikace.  
  
 K definování konkrétních verzí, na kterých běží vaše aplikace, přidejte jeden nebo více [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementy do vaší aplikace konfiguračního souboru. Každý `<supportedRuntime>` element uvádí podporovanou verzi modulu runtime s prvním zadání nejvíc preferovaný verze a poslední zadání nejméně upřednostňovanou verzi.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 Další informace najdete v tématu [postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).  
  
## <a name="version-compatibility-for-components"></a>Kompatibilita verzí pro součásti  
 Aplikace můžete řídit verzi rozhraní .NET Framework, na kterém běží, ale nemůže komponentu. Součásti a knihovny tříd se načetly v rámci konkrétní aplikace a proto na verzi rozhraní .NET Framework, který aplikace běží na automatické spouštění.  
  
 Z důvodu toto omezení zajištění kompatibility jsou zvlášť důležité pro součásti. Od verze rozhraní .NET Framework 4, můžete zadat úroveň, do kterého se očekává zůstane kompatibilní ve více verzí použitím komponentu <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> atribut tuto součást. Nástroje pro pomocí tohoto atributu lze zjistit, že případné porušení kompatibility zaručit v budoucích verzích komponenty.  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>Zpětná kompatibilita a rozhraní .NET Framework 4.5  
 Rozhraní .NET Framework 4.5 a novějších verzích je zpětně kompatibilní s aplikacemi, které byly vytvořeny v předchozích verzích rozhraní .NET Framework. Jinými slovy aplikace a součásti, které jsou vytvořené s předchozími verzemi bude fungovat bez úprav v rozhraní .NET Framework 4.5 a novějším. Však ve výchozím nastavení, aplikace spustit v verzi modulu CLR, pro které byly vyvinuty, takže možná budete muset zadat konfigurační soubor pro povolení aplikaci spustit v rozhraní .NET Framework 4.5 nebo novější verze. Další informace najdete v tématu [Kompatibilita verzí pro aplikace](#Apps) dříve v tomto článku.  
  
 V praxi, lze tuto kompatibility zjistit zdánlivě irelevantní změny v rozhraní .NET Framework a změny v programování techniky. Vylepšení výkonu v rozhraní .NET Framework 4.5 můžete například vystavit spor, který se nevyskytla v dřívějších verzích. Podobně pomocí pevně cesty k sestavení rozhraní .NET Framework, provádění porovnání rovnosti na konkrétní verzi rozhraní .NET Framework a získávání hodnota soukromé pole pomocí reflexe nejsou zpětně kompatibilní postupy. Kromě toho obsahuje každou verzi rozhraní .NET Framework oprav chyb a změny související se zabezpečením, které můžou ovlivnit kompatibilitu některé aplikace a součásti.  
  
 Pokud vaše aplikace nebo součást nefunguje podle očekávání na rozhraní .NET Framework 4.5 (včetně jeho verze bodu [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 nebo 4.7.1, použijte následující kontrolní seznamy:  
  
-  Pokud vaše aplikace byla vyvinuta spustit na libovolné verzi rozhraní .NET Framework od verze rozhraní .NET Framework 4.0, najdete v článku [kompatibilita aplikací v rozhraní .NET Framework](application-compatibility.md) vygenerovat seznam změn mezi vaší cílové verze rozhraní .NET Framework a verzi, na kterém aplikace běží.  

- Pokud máte aplikace rozhraní .NET Framework 3.5, také zobrazit [rozhraní .NET Framework 4 migrace problémy](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md).

- Pokud máte aplikace rozhraní .NET Framework 2.0, také zobrazit [změny v rozhraní .NET Framework 3.5 SP1](http://go.microsoft.com/fwlink/?LinkId=186989).

- Pokud máte aplikaci .NET Framework 1.1, také zobrazit [změny v rozhraní .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkID=125263).  
  
-   Pokud znovu kompilujete existující zdrojový kód pro spuštění v rozhraní .NET Framework 4.5 nebo jeho bod verze, nebo pokud vyvíjíte novou verzi aplikace nebo součásti, která je cílena [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo jeho bod uvolní z existující zdrojový kód základní, kontrola [ Co je zastaralé v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md) pro zastaralé typy a členy a použijte popsané řešení. (Dříve zkompilovaný kód bude pokračovat ke spouštění typy a členy, které byly označeny jako zastaralé.)  
  
-   Pokud zjistíte, že ke změně [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] funkční aplikaci, zkontrolujte [schéma nastavení běhového prostředí](../../../docs/framework/configure-apps/file-schema/runtime/index.md) k určení, zda může používat nastavení modulu runtime v konfiguračním souboru aplikace k obnovení předchozího chování.  
  
-   Pokud narazíte na problém, který není dokumentováno, souboru [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) a kontaktujte [ netfxcf@microsoft.com ](mailto:netfxcf@microsoft.com) s číslem chyby.  
  
## <a name="compatibility-and-side-by-side-execution"></a>Kompatibilita a souběžného zpracování  
 Pokud nemůže najít vhodné řešení svého problému, nezapomeňte, že běží node souběžně s verze 1.1, 2.0 a 3.5 rozhraní .NET Framework 4.5 (nebo jeden z jeho vydání bod) a je na místě aktualizaci, která nahrazuje verze 4. Pro aplikace, které cílí na verze 1.1, 2.0 a 3.5 můžete nainstalovat příslušnou verzi rozhraní .NET Framework na cílovém počítači a spusťte aplikaci v jeho nejlepší prostředí. Další informace o provádění vedle sebe, najdete v části [spuštění vedle sebe](../../../docs/framework/deployment/side-by-side-execution.md).  
  
## <a name="see-also"></a>Viz také  
 [Co je nového](../../../docs/framework/whats-new/index.md)  
 [Co je zastaralé v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Kompatibilita aplikací](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Zásadách životního cyklu podpory rozhraní Microsoft .NET Framework](http://go.microsoft.com/fwlink/p/?LinkId=248212)  
 [Problémy s migrací rozhraní .NET framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)
