---
title: 'Průvodce migrací na .NET Framework 4,8, 4,7, 4,6 a 4,5 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: 2fa992e1c0897d360f322581888c51dca8d8a734
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974975"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a>Průvodce migrací na .NET Framework 4,8, 4,7, 4,6 a 4,5

Pokud jste aplikaci vytvořili pomocí starší verze .NET Framework, můžete ji obecně upgradovat na .NET Framework 4,5 a jejich vydání (4.5.1 a 4.5.2), .NET Framework 4,6 a v jejích verzích (4.6.1 a 4.6.2), .NET Framework 4,7 a jejich verze v bodech ( 4.7.1 a 4.7.2) nebo je snadno .NET Framework 4,8. Otevřete projekt v aplikaci Visual Studio. Pokud byl projekt vytvořen v dřívější verzi sady Visual Studio, otevře se dialogové okno **Kompatibilita projektu** automaticky. Další informace o upgradu projektu v aplikaci Visual Studio naleznete v tématu [port, migrace a upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) a [cílení na platformu a kompatibilita platformy Visual Studio 2019](/visualstudio/releases/2019/compatibility).

 Některé změny v .NET Framework však vyžadují změny kódu. Můžete také využít výhody funkcí, které jsou novinkou v .NET Framework 4,5 a jeho vydání, v .NET Framework 4,6 a v jeho vydáních, v .NET Framework 4,7 a v jeho vydaných verzích nebo v .NET Framework 4,8. Provedení těchto typů změn aplikace pro novou verzi .NET Framework se obvykle označuje jako *migrace*. Pokud vaše aplikace nemusí být migrována, můžete ji spustit v .NET Framework 4,5 nebo novější verzi bez jejich opětovné kompilace.

## <a name="migration-resources"></a>Prostředky migrace

Před migrací aplikace z dřívějších verzí .NET Framework na verzi 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8 se podívejte na následující dokumenty:

- Podívejte se na [verze a závislosti](versions-and-dependencies.md) , abyste pochopili verzi CLR založenou na jednotlivých verzích .NET Framework a zkontrolovali pokyny pro úspěšné cílení na vaše aplikace.

- Přečtěte si informace o [kompatibilitě aplikací](application-compatibility.md) a zjistěte, jak se týkají prostředí runtime a změny cíle, které by mohly ovlivnit vaši aplikaci a jak je zpracovat.

- Přečtěte si, [co je zastaralé v knihovně tříd](../whats-new/whats-obsolete.md) a určete všechny typy nebo členy v kódu, které byly vytvořeny jako zastaralé, a Doporučené alternativy.

- Popis nových funkcí, které můžete chtít přidat do vaší aplikace, najdete v tématu [novinky](../whats-new/index.md) .

## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
- [Migrace z rozhraní .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Kompatibilita verzí](version-compatibility.md)
- [Verze a závislosti](versions-and-dependencies.md)
- [Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Co je nového](../whats-new/index.md)
- [Zastaralé položky v knihovně tříd](../whats-new/whats-obsolete.md)
- [.NET Framework oficiálních zásad podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Problémy s migrací rozhraní .NET Framework 4](net-framework-4-migration-issues.md)
