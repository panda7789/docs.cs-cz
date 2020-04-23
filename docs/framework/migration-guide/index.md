---
title: 'Průvodce migrací pro rozhraní .NET Framework 4.8, 4.7, 4.6 a 4.5 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: fbaee646f7adcfe1a53d4231790e4258fd95a892
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102629"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a>Migrace do rozhraní .NET Framework 4.8, 4.7, 4.6 a 4.5

Pokud jste aplikaci vytvořili pomocí starší verze rozhraní .NET Framework, můžete ji obecně upgradovat na rozhraní .NET Framework 4.5 a její bodové verze (4.5.1 a 4.5.2), rozhraní .NET Framework 4.6 a její bodové verze (4.6.1 a 4.6.2), rozhraní .NET Framework 4.7 a její bodové verze (4.7.1 a 4.7.2) nebo .NET Framework 4.8. Otevřete projekt v sadě Visual Studio. Pokud byl projekt vytvořen ve starší verzi sady Visual Studio, automaticky se otevře dialogové okno **Kompatibilita projektu.** Další informace o upgradu projektu v sadě Visual Studio najdete v [tématu Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) a Visual Studio [2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).

 Některé změny v rozhraní .NET Framework však vyžadují změny kódu. Můžete také využít funkce, která je nová v rozhraní .NET Framework 4.5 a jeho bodové verze, v rozhraní .NET Framework 4.6 a jeho bodových verzích, v rozhraní .NET Framework 4.7 a jeho bodových verzích nebo v rozhraní .NET Framework 4.8. Provádění těchto typů změn v aplikaci pro novou verzi rozhraní .NET Framework se obvykle označuje jako *migrace*. Pokud vaše aplikace nemusí být migrována, můžete ji spustit v rozhraní .NET Framework 4.5 nebo novější verzi bez její opětovné kompilace.

## <a name="migration-resources"></a>Prostředky migrace

Před migrací aplikace z dřívějších verzí rozhraní .NET Framework na verzi 4.5, 4.5.1, 4.5.2, 4.6, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 nebo 4.8 zkontrolujte následující dokumenty:

- Informace o verzi a závislostech naleznete v tématu [Verze a závislosti,](versions-and-dependencies.md) které jsou základem každé verze rozhraní .NET Framework, a přečtěte si pokyny pro úspěšné cílení na vaše aplikace.

- Zkontrolujte [kompatibilitu aplikací,](application-compatibility.md) abyste zjistili o změnách za běhu a retargetingu, které by mohly ovlivnit vaši aplikaci a jak s nimi zacházet.

- [Zkontrolujte, co je zastaralé v knihovně tříd](../whats-new/whats-obsolete.md) k určení všechny typy nebo členy v kódu, které byly zastaralé a doporučené alternativy.

- Informace o [novince](../whats-new/index.md) najdete v tématu Co je nového, které můžete chtít do aplikace přidat.

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
- [Migrace z rozhraní .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Kompatibilita verzí](version-compatibility.md)
- [Verze a závislosti](versions-and-dependencies.md)
- [Postup: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novějších verzí](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Co je nového](../whats-new/index.md)
- [Zastaralé položky v knihovně tříd](../whats-new/whats-obsolete.md)
- [Zásady oficiální podpory rozhraní .NET Framework](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Problémy s migrací rozhraní .NET Framework 4](net-framework-4-migration-issues.md)
