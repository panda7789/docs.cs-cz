---
title: 'Příručka k migraci na rozhraní .NET Framework 4.8, 4.7, 4.6 a 4.5 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb51a0be57992d65a88e958d76a5e371dc028a00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974958"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a>Příručka k migraci na rozhraní .NET Framework 4.8, 4.7, 4.6 a 4.5

Pokud jste aplikaci vytvořili pomocí starší verze rozhraní .NET Framework, můžete ho upgradovat obecně na rozhraní .NET Framework 4.5 a jeho verze (4.5.1 a 4.5.2), .NET Framework 4.6 a jeho vydání (4.6.1 a 4.6.2), .NET Framework 4.7 a jeho vydání) 4.7.1 a 4.7.2), nebo rozhraní .NET Framework 4.8 snadno. Otevřete svůj projekt v sadě Visual Studio. Pokud váš projekt byl vytvořen v dřívější verzi sady Visual Studio **kompatibilita projektu** automaticky otevře se dialogové okno. Další informace o upgradu projektu v sadě Visual Studio najdete v tématu [Port, migrace a Upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) a [Visual Studio. 2019 cílení na platformy a Kompatibilita](/visualstudio/releases/2019/compatibility).

 Nicméně některé změny v rozhraní .NET Framework vyžadují změny kódu. Můžete také využít výhod funkcí, které jsou nové v rozhraní .NET Framework 4.5 a jeho novější vydání, v rozhraní .NET Framework 4.6 a jeho novější vydání, v rozhraní .NET Framework 4.7 a jeho novější vydání nebo v rozhraní .NET Framework 4.8. Provedení těchto typů změn aplikace pro novou verzi rozhraní .NET Framework se obvykle označuje jako *migrace*. Pokud aplikace nemá být přenesena, můžete ji spustit v rozhraní .NET Framework 4.5 nebo novější verze bez opětovné kompilace.

## <a name="migration-resources"></a>Zdroje migrace

Před migrací vaší aplikace z předchozích verzí rozhraní .NET Framework verze 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 nebo 4.8, přečtěte si následující dokumenty:

- Zobrazit [verze a závislosti](versions-and-dependencies.md) pochopit verzi CLR v rámci každé verze rozhraní .NET Framework a kde naleznete pokyny pro úspěšné cílení na své aplikace.

- Kontrola [kompatibilita aplikací](application-compatibility.md) najdete informace o modulu runtime a změně cíle změn, které může mít vliv na vaše aplikace a způsob jejich zpracování.

- Kontrola [What's Obsolete in knihovny tříd](../whats-new/whats-obsolete.md) určit všechny typy nebo členy v kódu, které jsou již zastaralé a doporučené alternativy.

- Zobrazit [novinky](../whats-new/index.md) popisy nových funkcí, které chcete přidat do vaší aplikace.

## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
- [Migrace z rozhraní .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Kompatibilita verzí](version-compatibility.md)
- [Verze a závislosti](versions-and-dependencies.md)
- [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Co je nového](../whats-new/index.md)
- [Zastaralé položky v knihovně tříd](../whats-new/whats-obsolete.md)
- [Verze rozhraní .NET framework a informace o sestavení](https://go.microsoft.com/fwlink/?LinkId=201701)
- [Zásady životního cyklu podpory rozhraní Microsoft .NET Framework](https://go.microsoft.com/fwlink/?LinkId=196607)
- [Problémy s migrací rozhraní .NET Framework 4](net-framework-4-migration-issues.md)