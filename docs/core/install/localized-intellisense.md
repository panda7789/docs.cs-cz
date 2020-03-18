---
title: Instalace lokalizovaných souborů IntelliSense
description: Přečtěte si, jak nastavit vývojový počítač tak, aby používal lokalizované soubory IntelliSense pro projekty .NET Core v sadě Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157710"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a>Jak nainstalovat lokalizované soubory IntelliSense pro rozhraní .NET Core

[IntelliSense](/visualstudio/ide/using-intellisense) je podpora pro dokončení kódu, která je k dispozici v různých integrovaných vývojových prostředích (IDE), jako je například Visual Studio. Ve výchozím nastavení při vývoji projektů .NET Core sada SDK obsahuje pouze anglickou verzi souborů IntelliSense. Tento článek vysvětluje:

- Jak nainstalovat lokalizovanou verzi těchto souborů.
- Jak upravit instalaci sady Visual Studio tak, aby používala jiný jazyk.

## <a name="prerequisites"></a>Požadavky

- [Sada .NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.
- [Visual Studio 2019 verze 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější verze.

## <a name="download-and-install-the-localized-intellisense-files"></a>Stažení a instalace lokalizovaných souborů IntelliSense

> [!IMPORTANT]
> Tento postup vyžaduje, abyste měli oprávnění správce ke kopírování souborů IntelliSense do instalační složky Jádra .NET.

1. Přejděte na stránku [Stáhnout soubory IntelliSense.](https://dotnet.microsoft.com/download/dotnet-core/intellisense)

1. Stáhněte si soubor IntelliSense pro jazyk a verzi, kterou chcete použít.

1. Extrahujte obsah souboru zip.

1. Přejděte do složky .NET Core Intellisense.

   1. Přejděte do instalační složky jádra .NET. Ve výchozím nastavení je v části *%ProgramFiles%\dotnet\packs*.
   1. Zvolte, pro kterou sadu SDK chcete nainstalovat službu IntelliSense, a přejděte na přidruženou cestu. Máte následující možnosti:

      | Typ sady SDK        | Cesta                               |
      | --------------- | ---------------------------------- |
      | .NET Core       | *Soubor Microsoft.NETCore.App.ref*        |
      | Windows Desktop | *Microsoft.WindowsDesktop.App.Ref* |
      | .NET Standard   | *NETStandard.Library.Ref*          |

   1. Přejděte na verzi, pro kterou chcete nainstalovat lokalizovanou službu IntelliSense. Například *3.1.0*.
   1. Otevřete složku *ref.*
   1. Otevřete složku zástupné názvy. Například *netcoreapp3.1*.

   Úplná cesta, na kterou byste přešli, by tedy vypadala podobně jako *c:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.

1. Vytvořte podsložku uvnitř složky zástupný název, kterou jste právě otevřeli. Název složky označuje, který jazyk chcete použít. V následující tabulce jsou uvedeny různé možnosti:

   | Jazyk              | Název složky |
   | --------------------- | ----------- |
   | Brazilská portugalština  | *pt-br*     |
   | Čínština (zjednodušená)  | *zh-hans*   |
   | Čínština (tradiční) | *zh-hant*   |
   | Francouzština                | *Fr*        |
   | Němčina                | *De*        |
   | Italština               | *je to*        |
   | Japonština              | *ja*        |
   | Korejština                | *Ko*        |
   | Ruština               | *Ru*        |
   | Španělština               | *es*        |

1. Zkopírujte soubory *XML,* které jste extrahovali v kroku 3, do této nové složky. Soubory *XML* jsou rozděleny podle složek sady SDK, takže je zkopírujte do odpovídající sady SDK, kterou jste zvolili v kroku 4.

## <a name="modify-visual-studio-language"></a>Úprava jazyka sady Visual Studio

Aby visual studio používalo pro technologie IntelliSense jiný jazyk, nainstalujte příslušnou jazykovou sadu. To lze provést [během instalace](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) nebo později úpravou instalace sady Visual Studio. Pokud již máte Visual Studio nakonfigurované podle jazyka podle vašeho výběru, instalace technologie IntelliSense je připravena.

### <a name="install-the-language-pack"></a>Instalace jazykové sady

Pokud jste požadovanou jazykovou sadu během instalace nenainstalovali, aktualizujte sadu Visual Studio následujícím způsobem a nainstalujte ji:

> [!IMPORTANT]
> Chcete-li nainstalovat, aktualizovat nebo upravit visual studio, musíte se přihlásit pomocí účtu, který má oprávnění správce. Další informace naleznete [v tématu Uživatelská oprávnění a Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).

1. Vyhledejte instalační program sady Visual Studio v počítači.

   Například v počítači se systémem Windows 10 vyberte **start**a pak přejděte na písmeno **V**, kde je uvedeno jako **Instalační služba sady Visual Studio**.

   ![Otevření Instalační služby sady Visual Studio z Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Instalační program sady Visual Studio najdete také v následujícím umístění:
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Před pokračováním bude pravděpodobně nutné aktualizovat instalační program. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici sady Visual Studio, do které chcete přidat jazykovou sadu, a pak zvolte **Změnit**.

   ![Aktualizace nebo úprava sady Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > Pokud tlačítko **Změnit nevidíte,** ale místo toho se zobrazí **aktualizace,** je třeba před úpravou instalace aktualizovat visual studio.
   > Po dokončení aktualizace by se mělo zobrazit tlačítko **Změnit.**

1. Na kartě **Jazykové sady** vyberte nebo zrušte výběr jazyků, které chcete nainstalovat nebo odinstalovat.

   ![Karta jazykové sady Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. Zvolte **Změnit**. Aktualizace se spustí.

### <a name="modify-language-settings-in-visual-studio"></a>Změna nastavení jazyka v sadě Visual Studio

Po instalaci požadovaných jazykových sad upravte nastavení sady Visual Studio tak, aby používalo jiný jazyk:

1. Otevřete sadu Visual Studio.

1. V počátečním okně zvolte **Pokračovat bez kódu**.

1. Na řádku nabídek vyberte**Možnosti** **nástrojů** > . Otevře se dialogové okno Možnosti.

1. V uzlu **Prostředí** zvolte **Mezinárodní nastavení**.

1. V rozevíracím panelu **Jazyk** vyberte požadovaný jazyk. Vyberte **OK**.

1. Dialogové okno informuje, že je nutné restartovat visual studio pro změny se projeví. Vyberte **OK**.

1. Restartujte sadu Visual Studio.

Poté by měl váš technologie IntelliSense fungovat očekávaným způsobem při otevření projektu .NET Core, který se zaměřuje na verzi právě nainstalovaných souborů IntelliSense.

## <a name="see-also"></a>Viz také

- [Technologie IntelliSense v sadě Visual Studio](/visualstudio/ide/using-intellisense)
