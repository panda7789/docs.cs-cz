---
title: Nainstalovat lokalizované soubory IntelliSense
description: Naučte se, jak nastavit vývojový počítač tak, aby používal lokalizované soubory IntelliSense pro projekty .NET Core v sadě Visual Studio.
ms.date: 01/23/2020
ms.openlocfilehash: 58b462507edf953a6c28aadbb9e3239a5cbe05b2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733648"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a>Jak nainstalovat lokalizované soubory IntelliSense pro .NET Core

[IntelliSense](/visualstudio/ide/using-intellisense) je podpora dokončování kódu, která je k dispozici v různých integrovaných vývojových prostředích (IDES), jako je například Visual Studio. Ve výchozím nastavení, když vyvíjíte projekty .NET Core, sada SDK obsahuje pouze anglické verze souborů technologie IntelliSense. Tento článek vysvětluje:

- Jak nainstalovat lokalizované verze těchto souborů.
- Jak změnit instalaci sady Visual Studio tak, aby používala jiný jazyk.

## <a name="prerequisites"></a>Požadavky

- [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.
- [Visual Studio 2019 verze 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) nebo novější verze.

## <a name="download-and-install-the-localized-intellisense-files"></a>Stažení a instalace lokalizovaných souborů IntelliSense

> [!IMPORTANT]
> Tento postup vyžaduje, abyste měli oprávnění správce ke kopírování souborů IntelliSense do instalační složky .NET Core.

1. Přejít na stránku [stáhnout soubory IntelliSense](https://dotnet.microsoft.com/download/dotnet-core/intellisense) .

1. Stáhněte si soubor IntelliSense pro jazyk a verzi, kterou chcete použít.

1. Extrahujte obsah souboru ZIP.

1. Přejděte do složky .NET Core IntelliSense.

   1. Přejděte do instalační složky rozhraní .NET Core. Ve výchozím nastavení je to pod *%ProgramFiles%\dotnet\packs*.
   1. Vyberte sadu SDK, pro kterou chcete technologii IntelliSense nainstalovat, a přejděte k související cestě. Máte následující možnosti:

      | Typ sady SDK        | Cesta                               |
      | --------------- | ---------------------------------- |
      | .NET Core       | *Microsoft. NETCore. app. ref*        |
      | Windows Desktop | *Microsoft. WindowsDesktop. app. ref* |
      | .NET Standard   | *NETStandard. Library. ref*          |
   
   1. Přejděte do verze, pro kterou chcete nainstalovat lokalizovanou technologii IntelliSense. Například *3.1.0*.
   1. Otevřete složku *ref* .
   1. Otevřete složku moniker. Například *netcoreapp 3.1*.

   Úplná cesta, na kterou byste chtěli přejít, by tak vypadala podobně jako *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\3.1.0\ref\netcoreapp3.1*.

1. Vytvořte podsložku ve složce moniker, kterou jste právě otevřeli. Název složky určuje, který jazyk chcete použít. Následující tabulka uvádí různé možnosti:

   | Jazyk              | Název složky |
   | --------------------- | ----------- |
   | Brazilská portugalština  | *pt – br*     |
   | Čínština (zjednodušená)  | *zh – Hans*   |
   | Čínština (tradiční) | *zh – Hant*   |
   | Francouzština                | *FR*        |
   | Němčina                | *&*        |
   | Italština               | *její*        |
   | Japonština              | *dža*        |
   | Korejština                | *Ko*        |
   | Ruština               | *ru*        |
   | Španělština               | *jednomu*        |

1. Zkopírujte soubory *. XML* , které jste extrahovali v kroku 3, do této nové složky. Soubory *. XML* jsou rozdělené podle složek sady SDK, proto je zkopírujte do odpovídajícího SDK, kterou jste zvolili v kroku 4.

## <a name="modify-visual-studio-language"></a>Změnit jazyk sady Visual Studio

Aby sada Visual Studio používala pro technologii IntelliSense jiný jazyk, nainstalujte příslušnou jazykovou sadu. To lze provést v [průběhu instalace](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) nebo později úpravou instalace sady Visual Studio. Pokud již sadu Visual Studio nakonfigurovali pro zvolený jazyk, bude instalace technologie IntelliSense připravena.

### <a name="install-the-language-pack"></a>Nainstalovat jazykovou sadu

Pokud jste požadovanou jazykovou sadu neinstalovali během instalace, aktualizujte sadu Visual Studio podle následujících pokynů k instalaci jazykové sady:

> [!IMPORTANT]
> Chcete-li nainstalovat, aktualizovat nebo upravit aplikaci Visual Studio, je nutné se přihlásit pomocí účtu, který má oprávnění správce. Další informace naleznete v tématu [uživatelská oprávnění a aplikace Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).

1. Najdete instalační program sady Visual Studio v počítači.

   Například v počítači se systémem Windows 10, vyberte **Start**a poté přejděte k označení **V**, kde je hodnota uvedena jako **instalační program sady Visual Studio**.

   ![Otevřete Instalační program pro Visual Studio z Windows](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Instalační program pro Visual Studio můžete najít také v následujícím umístění:
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Než budete pokračovat, bude pravděpodobně nutné aktualizovat instalační program. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici sady Visual Studio, do které chcete přidat jazykovou sadu, a pak zvolte možnost **Upravit**.

   ![Aktualizace nebo změna sady Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > Pokud nevidíte tlačítko **Upravit** , ale místo toho se zobrazí **aktualizace** , budete muset Visual Studio aktualizovat předtím, než budete moct instalaci upravit.
   > Po dokončení aktualizace by se mělo zobrazit tlačítko **Upravit** .

1. Na kartě **jazykové sady** vyberte nebo zrušte výběr jazyků, které chcete nainstalovat nebo odinstalovat.

   ![Karta jazykové sady sady Visual Studio](./media/localized-intellisense/vs-modify-language-packs.png)

1. Klikněte na tlačítko **Upravit**. Spustí se aktualizace.

### <a name="modify-language-settings-in-visual-studio"></a>Úprava nastavení jazyka v aplikaci Visual Studio

Jakmile nainstalujete požadované jazykové sady, upravte nastavení aplikace Visual Studio tak, aby používalo jiný jazyk:

1. Otevřít Visual Studio.

1. V okně Start vyberte možnost **pokračovat bez kódu**.

1. Na panelu nabídek vyberte možnost **nástroje** > **Možnosti**. Otevře se dialogové okno Možnosti.

1. V uzlu **prostředí** vyberte možnost **mezinárodní nastavení**.

1. V rozevíracím seznamu **jazyk** vyberte požadovaný jazyk. Vyberte **OK**. 

1. Dialog vás informuje o tom, že je nutné restartovat aplikaci Visual Studio, aby se změny projevily. Vyberte **OK**.

1. Restartujte sadu Visual Studio.

Poté by měla technologie IntelliSense fungovat podle očekávání, když otevřete projekt .NET Core, který cílí na verzi souborů technologie IntelliSense, které jste právě nainstalovali.

## <a name="see-also"></a>Viz také:

- [IntelliSense v aplikaci Visual Studio](/visualstudio/ide/using-intellisense)
