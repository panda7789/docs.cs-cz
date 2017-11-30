---
title: "Jaký & č. 39; s zastaralé v knihovně tříd rozhraní .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4560988445b91939deef84211a1c8c13ed938560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="what39s-obsolete-in-the-net-framework-class-library"></a>Jaký & č. 39; s zastaralé v knihovně tříd rozhraní .NET Framework
Rozhraní .NET Framework se mění v čase. Každá nová verze přidává nové typy a členy typu, které přinášejí nové funkce. Existující typy a jejich členové také časem změnit. Například některé typy stane méně důležité, jako je technologie, které podporují nahrazena novou technologií a některé metody nejsou k dispozici novější metody, které jsou vhodnější nebo obsáhlejší.  
  
 Rozhraní .NET Framework a modul common language runtime usilují o podporu zpětné kompatibility (povolení aplikace vyvinuté pomocí jedné verze rozhraní .NET Framework ke spuštění na další verzi rozhraní .NET Framework). Díky tomu je obtížné stačí odstranit určitý typ nebo člen typu. Místo toho rozhraní .NET Framework označuje, že typ nebo člen typu by už použít označením jako zastaralé nebo zastaralé. Místo začne typ nebo člen zahrnuje označením tak, aby vývojáři víte ho bude odstraněn a čas reagovat na jeho odstranění. Existující kód, který používá typ nebo člen je však nadále spuštěna v nové verzi rozhraní .NET Framework.  
  
> [!NOTE]
>  Podmínky *zastaralé* a *zastaralé* mají stejný význam při aplikování typy a členy rozhraní .NET Framework.  
  
## <a name="the-obsoleteattribute-attribute"></a>Atribut ObsoleteAttribute  
 Rozhraní .NET Framework označuje, že typ nebo typ člena je zastaralé se s označením <xref:System.ObsoleteAttribute> atribut. Použití atributu pro typ nebo člen označuje, že typ nebo člen se odeberou v některé budoucí verzi rozhraní .NET Framework bez narušení zkompilovaný kód, který použije tento člen.  
  
 Kromě indikující, že typ nebo typ člena je neplatný, <xref:System.ObsoleteAttribute> definuje, jak kompilátor zpracovává zdrojový kód, který obsahuje tento typ nebo člen. Kompilátor můžete zkompilovat kód, ale také posílat upozornění, nebo použijte typ nebo člen může považovat za chybu. V prvním případě můžete úspěšně zkompilovat kód, ale upozornění označuje, že typ nebo člen je zastaralé. V druhém případě kompilace se nezdaří.  
  
 I když kompilace vytvoří chybu místo zprávu upozornění <xref:System.ObsoleteAttribute> nemá vliv na chování. Aplikace, které používají typ nebo člen a byly úspěšně zkompilovány tedy bude vždy úspěšně spuštěna. Jenom se nezdaří pokus o znovu zkompiluje aplikaci, která používá typ nebo člen.  
  
## <a name="how-to-handle-obsolete-types-and-members"></a>Postupy: zpracování zastaralé typy a členy  
 Při upgradu a znovu zkompiluje stávající kód, pomocí neplatný typ nebo člen, který vyvolá upozornění kompilátoru v aplikaci je zcela přijatelné. Ale přečtěte si upozornění kompilátoru k určení, zda byste měli změnit kód aplikace. Pokud zpráva neukazuje na jinou vhodnou alternativu, proveďte jednu z těchto věcí:  
  
-   Změna kódu odebráním použití typ nebo člen, pokud je to možné.  
  
     -nebo-  
  
-   Najdete v dokumentaci k této technologické oblasti určit, jak reagovat na zastaralá.  
  
 Můžete se rozhodnout nechcete znovu zkompiluje existující kód proti novější verzi rozhraní .NET Framework. Místo toho můžete zadat verzi rozhraní .NET Framework, vůči které stávající zkompilovaný kód běží. Předpokládejme například, že máte aplikaci s názvem app1.exe, který se zkompiluje proti [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], ale chcete, aby aplikace ke spouštění [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. To vyžaduje následující kroky:  
  
1.  Vytvořte konfigurační soubor pro váš hlavní spustitelný soubor s názvem *appName*. exe.config, kde *appName* je název spustitelného souboru aplikace. Pro aplikaci s názvem app1.exe v našem příkladu by vytvořit konfigurační soubor s názvem app1.exe.config.  
  
2.  Přidejte následující do konfiguračního souboru.  
  
    ```xml  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 Následující tabulka uvádí řetězcové hodnoty, které lze přiřadit `version` atribut k cílení na konkrétní verzi rozhraní .NET Framework.  
  
|Verze rozhraní .NET Framework|`version`řetězec|
|-|-|  
|4.7 (včetně 4.7.1)|V4.0|  
|4.6 (včetně 4.6.1 a 4.6.2)|V4.0|  
|4.5 (včetně 4.5.1 a 4.5.2)|V4.0|  
|4|V4.0|  
|3.5|v2.0.50727|  
|2.0|v2.0.50727|  
|1.1|V1.1.4322|  
|1.0|V1.0.3705|  
  
## <a name="obsolete-lists-for-the-net-framework-45-and-46"></a>Zastaralé seznamy pro rozhraní .NET Framework 4.5 a 4.6  
 [Zastaralé typy](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [Zastaralé členy](../../../docs/framework/whats-new/obsolete-members.md)  
  
## <a name="obsolete-lists-for-previous-versions"></a>Zastaralé seznamy pro předchozí verze  
 [Zastaralé typy v rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [Zastaralé členy v rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [Zastaralý seznam rozhraní .NET framework 3.5](http://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [Zastaralý seznam rozhraní .NET framework 2.0](http://go.microsoft.com/fwlink/?LinkID=125264)  
  
## <a name="see-also"></a>Viz také  
 [\<supportedRuntime > elementu](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
