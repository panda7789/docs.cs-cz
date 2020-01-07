---
title: Viz nainstalované aktualizace zabezpečení a opravy hotfix pro .NET Framework.
description: Zjistěte, jak určit, které .NET Framework aktualizace zabezpečení a opravy hotfix jsou nainstalovány v počítači.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 498462b2dc5f0e63562cb52699460e0d37fd4a60
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342288"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Jak určit, které .NET Framework aktualizace zabezpečení a opravy hotfix jsou nainstalovány

V tomto článku se dozvíte, jak zjistit, které .NET Framework aktualizace zabezpečení a opravy hotfix jsou nainstalovány v počítači.

> [!NOTE]
> Všechny techniky uvedené v tomto článku vyžadují účet s oprávněními správce.

## <a name="use-registry-editor"></a>Použití Editoru registru

Nainstalované aktualizace zabezpečení a opravy hotfix pro každou verzi .NET Framework nainstalované na počítači jsou uvedené v registru Windows. K zobrazení těchto informací můžete použít program Editor registru (*Regedit. exe*).

1. Spusťte program **Regedit. exe**. V systému Windows 8 a novějších verzích klikněte pravým tlačítkem myši na **Start** ![snímku loga Windows Key.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo")a pak vyberte **Spustit**. Do pole **otevřít** zadejte **Regedit** a vyberte **OK**.

2. V editoru registru otevřete následující podklíč:

     **HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Updates**

     Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují. Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).

V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích. Informace o zjištění čísel nainstalovaných verzí najdete v tématu [Postup: určení, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).

## <a name="query-the-registry-using-code"></a>Dotazování registru pomocí kódu

Následující příklad programově určuje .NET Framework aktualizace zabezpečení a opravy hotfix, které jsou nainstalovány v počítači:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Příklad vytvoří výstup podobný následujícímu:

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

## <a name="use-powershell-to-query-the-registry"></a>Použití PowerShellu k dotazování registru

Následující příklad ukazuje, jak určit .NET Framework aktualizace zabezpečení a opravy hotfix, které jsou nainstalovány na počítači pomocí prostředí PowerShell:

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

Příklad vytvoří výstup podobný následujícímu:

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

## <a name="see-also"></a>Viz také:

- [Postupy: určení, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md)
- [Instalace .NET Framework pro vývojáře](../install/guide-for-developers.md)
- [Verze a závislosti](versions-and-dependencies.md)
