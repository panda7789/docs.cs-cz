---
title: Řešení potíží s touto aplikací nelze spustit.
description: Přečtěte si, co dělat, když se zobrazí dialogové okno Tato aplikace nelze spustit.
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965903"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Poradce při potížích s chybovou zprávou Tuto aplikaci nelze spustit

Aplikace vyvinuté pro rozhraní .NET Framework obvykle vyžadují, aby byla v systému nainstalována určitá verze rozhraní .NET Framework. V některých případech se můžete pokusit spustit aplikaci bez nainstalované verze nebo očekávané verze rozhraní .NET Framework. To často vytváří chybové dialogové okno, jako je následující:

![Tuto aplikaci nelze spustit.](media/application-not-started/app-could-not-be-started.png)

To obvykle označuje jednu z následujících podmínek:

- Instalace rozhraní .NET Framework v systému byla poškozena.

- Nelze zjistit verzi rozhraní .NET Framework, kterou vaše aplikace potřebuje.

Chcete-li tento problém vyřešit, abyste mohli aplikaci spustit, postupujte takto:

1. Stáhněte si [nástroj .NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135). Nástroj se spustí automaticky po dokončení stahování.

1. Pokud nástroj pro opravu rozhraní .NET Framework doporučuje jakoukoli další akci, například akci uvedenou na následujícím obrázku, vyberte **další**.

   ![Doporučené změny](media/application-not-started/repair-tool-recommended-changes.png)

1. Nástroje pro opravu rozhraní .NET Framework zobrazí dialogové okno zobrazené na následujícím obrázku, které označuje, že změny jsou dokončeny. Chcete-li zkusit znovu spustit aplikaci, ponechejte dialogové okno otevřené. To by mělo být úspěšné, pokud nástroj .NET Framework Repair Tool identifikoval a opravil poškozenou instalaci rozhraní .NET Framework.

   ![Doporučené změny](media/application-not-started/repair-tool-changes-complete.png)

1. Pokud se aplikace úspěšně spustí, vyberte tlačítko **Dokončit.** V opačném případě vyberte tlačítko **Další.**

1. Pokud jste vybrali tlačítko **Další,** nástroj pro opravu rozhraní .NET Framework zobrazí dialogové okno, jako je následující. Chcete-li společnosti Microsoft odeslat diagnostické informace, vyberte tlačítko **Dokončit.**

   ![Problém nelze vyřešit.](media/application-not-started/repair-tool-no-resolution.png)

1. Pokud aplikaci stále nemůžete spustit, nainstalujte nejnovější verzi rozhraní .NET Framework podporovanou vaší verzí systému Windows, jak je znázorněno v následující tabulce.

   |Verze systému Windows|Instalace rozhraní .NET Framework|
   |---|---|
   |Aktualizace Windows 10 Anniversary update a novější verze|[Doba běhu rozhraní .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, Listopadová aktualizace Windows 10|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[Doba běhu rozhraní .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 SP1|[Doba běhu rozhraní .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > Rozhraní .NET Framework 4.8 je předinstalováno v aktualizaci Windows 10 z května 2019.

1. Pokus o spuštění aplikace.

1. V některých případech se může zobrazit dialogové okno, jako je následující, které vás požádá o instalaci rozhraní .NET Framework 3.5. Vyberte **Stáhnout a nainstalujte tuto funkci,** nainstalujte rozhraní .NET Framework 3.5 a potom aplikaci znovu spusťte.

   ![Problém nelze vyřešit.](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Viz také

- [Požadavky na systém rozhraní .NET Framework](../get-started/system-requirements.md)
- [Instalační příručka rozhraní .NET Framework](index.md)
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
