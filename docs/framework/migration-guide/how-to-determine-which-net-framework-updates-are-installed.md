---
title: Viz nainstalované aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix
description: Přečtěte si, jak určit, které aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix jsou v počítači nainstalovány.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181272"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Jak zjistit, které aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix jsou nainstalovány

V tomto článku se dozvíte, které aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix jsou v počítači nainstalovány.

> [!NOTE]
> Všechny techniky uvedené v tomto článku vyžadují účet s oprávněními správce.

## <a name="use-registry-editor"></a>Použít Editor registru

Nainstalované aktualizace zabezpečení a opravy hotfix pro každou verzi rozhraní .NET Framework nainstalovaných v počítači jsou uvedeny v registru systému Windows. K zobrazení těchto informací můžete použít program Editor registru (*regedit.exe*).

1. Otevřete program **regedit.exe**. Ve Windows 8 a novějších verzích klikněte pravým tlačítkem **Run**myši na **položku Spustit** ![snímek obrazovky loga klíče systému Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo") Do pole **Otevřít** zadejte **regedit** a vyberte **OK**.

2. V editoru registru otevřete následující podklíč:

     **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**

     Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují. Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).

V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích. Informace o zjišťování nainstalovaných čísel verzí naleznete v [tématu Postup: Určení, které verze rozhraní .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).

## <a name="query-the-registry-using-code"></a>Dotaz na registr pomocí kódu

Následující příklad programově určuje aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix nainstalované v počítači:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Příklad vytvoří výstup, který je podobný následujícímu:

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="use-powershell-to-query-the-registry"></a>Použití prostředí PowerShell k dotazování registru

Následující příklad ukazuje, jak určit aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix nainstalované v počítači pomocí prostředí PowerShell:

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){

   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

Příklad vytvoří výstup, který je podobný následujícímu:

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a>Viz také

- [Postup: Určení nainstalovaných verzí rozhraní .NET Framework](how-to-determine-which-versions-are-installed.md)
- [Instalace rozhraní .NET Framework pro vývojáře](../install/guide-for-developers.md)
- [Verze a závislosti](versions-and-dependencies.md)
