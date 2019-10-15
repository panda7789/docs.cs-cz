---
title: Řešení potíží "tuto aplikaci nebylo možné spustit"
description: Přečtěte si, co dělat, když se zobrazí dialogové okno "Tato aplikace se nedá spustit".
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2019
ms.openlocfilehash: 8fa8381f1b05445f259b4e4af5cc17fa487b2ce0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319171"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Řešení potíží s chybovou zprávou "tuto aplikaci nebylo možné spustit"

Aplikace, které jsou vyvíjené pro .NET Framework obvykle vyžadují, aby byla v systému nainstalovaná určitá verze .NET Framework. V některých případech se můžete pokusit spustit aplikaci, aniž by byla nainstalována buď nainstalovaná verze, nebo očekávaná verze .NET Framework. Tím se často vytvoří chybové dialogové okno podobné následujícímu:

![Tuto aplikaci nebylo možné spustit.](media/application-not-started/app-could-not-be-started.png)

To obvykle znamená jednu z následujících podmínek:

- Instalace .NET Framework v systému se stala poškozená.

- Verze .NET Framework potřebná vaší aplikací nebyla zjištěna.

Chcete-li tento problém vyřešit, abyste mohli spustit aplikaci, postupujte následovně:

1. Stáhněte si [Nástroj pro opravu .NET Framework (NetFxRepairTool. exe)](https://www.microsoft.com/download/details.aspx?id=30135). Nástroj se spustí automaticky po dokončení stahování.

1. Pokud nástroj pro opravu .NET Framework doporučuje jakékoli další akce, jako například na následujícím obrázku, vyberte možnost **Další**.

   ![Doporučené změny](media/application-not-started/repair-tool-recommended-changes.png)

1. Nástroje .NET Framework pro opravu zobrazí dialogové okno zobrazené na následujícím obrázku, které indikuje, že se změny dokončily. Nechejte dialogové okno otevřené a zkuste znovu spustit aplikaci. To by mělo být úspěšné, pokud nástroj pro opravu .NET Framework identifikoval a opravil poškozenou instalaci .NET Framework.

   ![Doporučené změny](media/application-not-started/repair-tool-changes-complete.png)

1. Pokud vaše aplikace funguje úspěšně, vyberte tlačítko **Dokončit** . V opačném případě klikněte na tlačítko **Další** .

1. Pokud jste vybrali tlačítko **Další** , nástroj .NET Framework pro opravu zobrazí dialogové okno podobné následujícímu. Kliknutím na tlačítko **Dokončit** odešlete diagnostické informace společnosti Microsoft.

   ![Nepovedlo se vyřešit problém.](media/application-not-started/repair-tool-no-resolution.png)

1. Pokud stále nemůžete aplikaci spustit, nainstalujte nejnovější verzi .NET Framework, kterou podporuje vaše verze Windows, jak je znázorněno v následující tabulce.

   |Verze Windows|Instalace .NET Framework|
   |---|---|
   |Windows 10 – aktualizace pro výročí a novější verze|[Modul runtime .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, listopadová aktualizace Windows 10|[.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345)|
   |Windows 8.1|[Modul runtime .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981)|
   |Windows 7 SP1|[Modul runtime .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4,6](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   > .NET Framework 4,8 je předinstalována ve Windows 10 – 2019 aktualizace.

1. Pokus o spuštění aplikace.

1. V některých případech se může zobrazit dialogové okno podobné následujícímu, které vás vyzve k instalaci .NET Framework 3,5. Vyberte **Stáhnout a nainstalovat tuto funkci** , pokud chcete nainstalovat .NET Framework 3,5, a pak aplikaci znovu spusťte.

   ![Nepovedlo se vyřešit problém.](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Viz také:

- [.NET Framework požadavky na systém](../get-started/system-requirements.md)
- [Průvodce instalací .NET Framework](index.md)
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
