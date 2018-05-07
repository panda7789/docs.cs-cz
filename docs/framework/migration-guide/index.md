---
title: 'Příručka k migraci na rozhraní .NET Framework 4.7, 4.6 a 4.5 '
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8ef6d73aa6cd044cf6808878bf6142a735d015c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>Příručka k migraci na rozhraní .NET Framework 4.7, 4.6 a 4.5 
Pokud jste vytvořili vaší aplikaci pomocí dřívější verze rozhraní .NET Framework, můžete obvykle ho upgradovat na rozhraní .NET Framework 4.5 nebo jeho verze bodu (4.5.1 a 4.5.2), rozhraní .NET Framework 4.6 a jeho verze bodu (4.6.1 a 4.6.2), nebo 4.7 rozhraní .NET Framework a jeho bod snadno uvolní (4.7.1 a 4.7.2). Otevřete projekt v sadě Visual Studio. Pokud váš projekt byla vytvořena ve starší verzi sady Visual Studio **projektu kompatibility** automaticky otevře dialogové okno. Další informace o upgradu na projekt v sadě Visual Studio najdete v tématu [Port, migrace a Upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) a [Visual Studio 2017 cílení a kompatibilita platformy](/visualstudio/productinfo/vs2017-compatibility-vs).  
  
 Ale některé změny v rozhraní .NET Framework vyžadovat změny vašeho kódu. Můžete také využít výhod funkcí, které je nového v rozhraní .NET Framework 4.5 a jeho verze bod, v rozhraní .NET Framework 4.6 a jeho verze bodu nebo ve 4.7 rozhraní .NET Framework a jeho bod uvolní. Provedením těchto typů změn do vaší aplikace pro novou verzi rozhraní .NET Framework se obvykle označuje jako *migrace*. Pokud aplikace nemá být provedena migrace, můžete ho spustit v rozhraní .NET Framework 4.5 nebo novější verze bez nutnosti rekompilace ho.  
  
## <a name="migration-resources"></a>Migrace prostředků  
 Před migrací aplikace z dřívějších verzí rozhraní .NET Framework verze 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2, projděte si následující dokumenty:  
  
-   V tématu [verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md) abyste pochopili základní každou verzi rozhraní .NET Framework verze CLR a přečtěte si pokyny pro cílení na aplikace úspěšně.  
  
-   Zkontrolujte [kompatibilita aplikací](../../../docs/framework/migration-guide/application-compatibility.md) informace o modulu runtime a odlišnosti ve změnách, které mohou ovlivnit vaše aplikace a jak bude zpracováván je cílení.  
  
-   Zkontrolujte [co je zastaralé v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md) určit všechny typy nebo členy v váš kód, které jsou již zastaralé a doporučených alternativách.  
  
-   V tématu [co je nového](../../../docs/framework/whats-new/index.md) popis nové funkce, které chcete přidat do vaší aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Kompatibilita aplikací](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Kompatibilita verzí](../../../docs/framework/migration-guide/version-compatibility.md)  
 [Verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Co je nového](../../../docs/framework/whats-new/index.md)  
 [Zastaralé položky v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Informace o sestavení a verze rozhraní .NET framework](http://go.microsoft.com/fwlink/?LinkId=201701)  
 [Microsoft .NET Framework podporu životního cyklu zásad](http://go.microsoft.com/fwlink/?LinkId=196607) [problémy migrace v rozhraní .NET Framework 4](net-framework-4-migration-issues.md)
