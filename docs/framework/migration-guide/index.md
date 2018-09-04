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
ms.openlocfilehash: fc3796e3e79112b14d45bb410e63656a81d474c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526717"
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>Příručka k migraci na rozhraní .NET Framework 4.7, 4.6 a 4.5 
Pokud jste aplikaci vytvořili pomocí starší verze rozhraní .NET Framework, obecně upgradem ji na verzi rozhraní .NET Framework 4.5 a jeho novější vydání (4.5.1 a 4.5.2), rozhraní .NET Framework 4.6 a jeho novější vydání (4.6.1 a 4.6.2), nebo rozhraní .NET Framework 4.7 a jeho bod snadno uvolní (4.7.1 a 4.7.2). Otevřete svůj projekt v sadě Visual Studio. Pokud váš projekt byl vytvořen v dřívější verzi sady Visual Studio **kompatibilita projektu** automaticky otevře se dialogové okno. Další informace o upgradu projektu v sadě Visual Studio najdete v tématu [Port, migrace a Upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) a [Visual Studio 2017 cílení na platformy a Kompatibilita](/visualstudio/productinfo/vs2017-compatibility-vs).  
  
 Nicméně některé změny v rozhraní .NET Framework vyžadují změny kódu. Můžete také využít výhod funkcí, které jsou nové v rozhraní .NET Framework 4.5 a jeho novější vydání, v rozhraní .NET Framework 4.6 a jeho novější vydání nebo v rozhraní .NET Framework 4.7 a jeho verze. Provedení těchto typů změn aplikace pro novou verzi rozhraní .NET Framework se obvykle označuje jako *migrace*. Pokud aplikace nemá být přenesena, můžete ji spustit v rozhraní .NET Framework 4.5 nebo novější verze bez opětovné kompilace.  
  
## <a name="migration-resources"></a>Zdroje migrace  
 Před migrací vaší aplikace z předchozích verzí rozhraní .NET Framework verze 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2, přečtěte si následující dokumenty:  
  
-   Zobrazit [verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md) pochopit verzi CLR v rámci každé verze rozhraní .NET Framework a kde naleznete pokyny pro úspěšné cílení na své aplikace.  
  
-   Kontrola [kompatibilita aplikací](../../../docs/framework/migration-guide/application-compatibility.md) najdete informace o modulu runtime a změně cíle změn, které může mít vliv na vaše aplikace a způsob jejich zpracování.  
  
-   Kontrola [What's Obsolete in knihovny tříd](../../../docs/framework/whats-new/whats-obsolete.md) určit všechny typy nebo členy v kódu, které jsou již zastaralé a doporučené alternativy.  
  
-   Zobrazit [novinky](../../../docs/framework/whats-new/index.md) popisy nových funkcí, které chcete přidat do vaší aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Kompatibilita aplikací](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Kompatibilita verzí](../../../docs/framework/migration-guide/version-compatibility.md)  
 [Verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Co je nového](../../../docs/framework/whats-new/index.md)  
 [Zastaralé položky v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Verze rozhraní .NET framework a informace o sestavení](https://go.microsoft.com/fwlink/?LinkId=201701)  
 [Zásady životního cyklu podpory .NET Framework společnosti Microsoft](https://go.microsoft.com/fwlink/?LinkId=196607) [problémy s migrací rozhraní .NET Framework 4](net-framework-4-migration-issues.md)
