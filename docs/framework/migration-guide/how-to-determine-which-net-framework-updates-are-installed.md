---
title: 'Postupy: Zjistit, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalované.'
description: Zjistěte, jak určit, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalovány v počítači.
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
ms.openlocfilehash: e11b2588471e95b4e47fd0efaf41757430b9bb39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604181"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Postupy: Zjistit, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalované.

V tomto článku se dozvíte, jak zjistit aktualizace zabezpečení, které rozhraní .NET Framework a opravy hotfix jsou nainstalované v počítači.

> [!NOTE]
> Všechny postupy uvedené v tomto článku vyžadovat účet s oprávněními správce.

## <a name="to-find-installed-updates-using-the-registry"></a>Vyhledání nainstalovaných aktualizací pomocí registru

Nainstalované aktualizace a opravy hotfix pro každou verzi rozhraní .NET Framework nainstalované v počítači jsou uvedeny v registru Windows. Můžete použít Editor registru (*regedit.exe*) program, chcete-li zobrazit tyto informace.

1. Otevřete program **regedit.exe**. V systému Windows 8 a novějších verzích, klikněte pravým tlačítkem na **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")a pak vyberte **spustit**. V **otevřít** zadejte **regedit** a vyberte **OK**.

2. V editoru registru otevřete následující podklíč:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují. Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).

V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích. Informace o způsobu zjištění čísel nainstalovaných verzí, naleznete v tématu [jak: Určete, jaké verze rozhraní .NET Framework jsou nainstalovány](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Chcete-li najít nainstalované aktualizace dotazem na registr v kódu

Následující příklad programově určuje aktualizace rozhraní .NET Framework zabezpečení a opravy hotfix, které jsou nainstalovány v počítači:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Vzorové postupy výstupu, který je podobný následujícímu:

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Chcete-li najít nainstalované aktualizace dotazem na registr v prostředí PowerShell

Následující příklad ukazuje, jak určit rozhraní .NET Framework aktualizací a oprav hotfix, které jsou nainstalovány v počítači pomocí Powershellu:

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

Vzorové postupy výstupu, který je podobný následujícímu:

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

- [Postupy: Zjištění nainstalovaných verzí rozhraní .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)
- [Instalace rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)
- [Verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md)
