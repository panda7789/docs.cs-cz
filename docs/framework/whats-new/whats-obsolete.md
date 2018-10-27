---
title: Co&#39;s zastaralé v knihovně tříd rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58ef462fdccc31a7694721b3ab9c3bec52d66abe
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183474"
---
# <a name="what39s-obsolete-in-the-net-framework-class-library"></a>Co&#39;s zastaralé v knihovně tříd rozhraní .NET Framework
Rozhraní .NET Framework mění v průběhu času. Každá nová verze přidá nové typy a členy typů, které přinášejí nové funkce. Existující typy a členové také v průběhu času měnit. Například některé typy se stanou méně důležité technologie, které podporují je nahrazena novou technologii a některé metody jsou nahrazena novější metody, které jsou vhodnější nebo více plně funkční.  
  
 Rozhraní .NET Framework a modulu common language runtime usilují o podporu zpětné kompatibility (povolení aplikace, které byly vyvinuty s jednu verzi rozhraní .NET Framework pro spuštění na další verzi rozhraní .NET Framework). Díky tomu je obtížné odebrat typ nebo člen typu. Místo toho rozhraní .NET Framework označuje, že typ nebo člen typu by už použita označením jako zastaralé nebo zastaralé. Ukončení podpory pro typ nebo člen zahrnuje označíte, aby vývojáři povědomí bude odchází a dostatek času reagovat na jeho odstranění. Existující kód, který používá typ nebo člen však nadále spuštěna v nové verzi rozhraní .NET Framework.  
  
> [!NOTE]
>  Podmínky *zastaralé* a *zastaralé* mají stejný význam při použití k typům a členům rozhraní .NET Framework.  
  
## <a name="the-obsoleteattribute-attribute"></a>Atribut ObsoleteAttribute  
 Rozhraní .NET Framework označuje, že ho s označením je zastaralý typ nebo člen typu <xref:System.ObsoleteAttribute> atribut. Použití atributu na typ nebo člen označuje, že typ nebo člen se odebere v některé budoucí verzi rozhraní .NET Framework bez zásadní zkompilovat kód, který používá tento člen.  
  
 Kromě označující, že je zastaralý, typ nebo člen typu <xref:System.ObsoleteAttribute> definuje způsob, jakým kompilátor zpracovává zdrojový kód, který obsahuje tento typ nebo člen. Kompilátor může kompilovat kód, ale generování upozornění nebo užívání tento typ nebo člen může považovat za chybu. V prvním případě kód lze zkompilovat úspěšně, ale upozornění označuje, že tento typ nebo člen je zastaralý. V druhém případě kompilace se nezdaří.  
  
 I v případě kompilace dojde k chybě místo zprávu s upozorněním <xref:System.ObsoleteAttribute> nemá vliv na chování za běhu. Aplikace, které používají tento typ nebo člen a byly úspěšně zkompilovány tedy bude vždy úspěšně spuštěna. Pokus znovu zkompilovat aplikaci, která používá typ nebo člen selže.  
  
## <a name="how-to-handle-obsolete-types-and-members"></a>Způsob zpracování zastaralých typů a členů  
 Při upgradu a znovu zkompilovat existující kód, pomocí zastaralý typ nebo člen, který vede k upozornění překladače ve vaší aplikaci je zcela přijatelné. Nicméně byste měli zkontrolovat upozornění kompilátoru k určení, zda byste měli změnit kód vaší aplikace. Pokud zpráva neodkazuje na jinou vhodnou alternativu, proveďte jednu z následujících akcí:  
  
-   Změňte kód tak, že odeberete použití tento typ nebo člen, pokud je to možné.  
  
     -nebo-  
  
-   Projděte si dokumentaci pro tuto technologickou oblast, jak reagovat na vyřazení.  
  
 Můžete se znovu zkompilovat existující kód na novější verzi rozhraní .NET Framework. Místo toho můžete určit verzi rozhraní .NET Framework, proti kterému stávajících zkompilovaný kód běží. Předpokládejme například, že máte aplikaci s názvem app1.exe, která byla zkompilována proti [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], ale má aplikace spouštět [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. To vyžaduje následující kroky:  
  
1.  Vytvoření konfiguračního souboru pro hlavní spustitelný soubor a pojmenujte ho *appName*. exe.config, kde *appName* je název spustitelného souboru aplikace. Aplikace s názvem app1.exe v našem příkladu by vytvořit konfigurační soubor s názvem app1.exe.config.  
  
2.  Přidejte následující konfigurační soubor.  
  
    ```xml  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 V následující tabulce jsou uvedeny řetězcové hodnoty, které můžete přiřadit `version` atribut pro cílení na konkrétní verzi rozhraní .NET Framework.  
  
|Verze rozhraní .NET Framework|`version` řetězec|
|-|-|  
|4.7 (včetně 4.7.1 a 4.7.2)|V4.0|  
|4.6 (včetně 4.6.1 a 4.6.2)|V4.0|  
|4.5 (včetně 4.5.1 a 4.5.2)|V4.0|  
|4|V4.0|  
|3.5|v2.0.50727|  
|2.0|v2.0.50727|  
|1.1|V1.1.4322|  
|1.0|V1.0.3705|  
  
## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a>Zastaralé seznamy pro rozhraní .NET Framework 4.5 a novější verze  
 [Zastaralé typy](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [Zastaralé členy](../../../docs/framework/whats-new/obsolete-members.md)  
  
## <a name="obsolete-lists-for-previous-versions"></a>Zastaralé seznamy pro předchozí verze  
 [Zastaralé typy v rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [Zastaralé členy v rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [Seznam zastaralých rozhraní .NET framework 3.5](https://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [Seznam zastaralých rozhraní .NET framework 2.0](https://go.microsoft.com/fwlink/?LinkID=125264)  
  
## <a name="see-also"></a>Viz také  
 [\<supportedRuntime > – Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
