---
title: 'Postupy: určení, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalovány.'
description: Zjistěte, jak určit, které aktualizace zabezpečení rozhraní .NET Framework a opravy hotfix jsou nainstalovány v počítači.
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
ms.openlocfilehash: 6373def6859023377bf899f02d710c2ac6d83c44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389597"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Postupy: určení, které rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix jsou nainstalovány.

Tento článek ukazuje, jak zjistit zabezpečení rozhraní .NET Framework, které aktualizace a opravy hotfix jsou nainstalovány v počítači.

> [!NOTE]
> Všechny postupy uvedené v tomto článku vyžadují účet s oprávněními správce.

## <a name="to-find-installed-updates-using-the-registry"></a>Najít nainstalované aktualizace pomocí klíče registru

Aktualizace nainstalované zabezpečení a opravy hotfix pro každou verzi rozhraní .NET Framework, který je nainstalován v počítači jsou uvedeny v registru systému Windows. Můžete použít Editor registru (*regedit.exe*) programu, který chcete zobrazit tyto informace.

1. Otevřete program **regedit.exe**. Ve Windows 8 a novější verze, klikněte pravým tlačítkem na **spustit** ![s logem Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), pak vyberte **spustit**. V **otevřete** zadejte **regedit** a vyberte **OK**.

2. V editoru registru otevřete následující podklíč:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Nainstalované aktualizace jsou uvedeny v podklíčích, které určují verzi rozhraní .NET Framework, na kterou se vztahují. Jednotlivé aktualizace jsou označeny číslem znalostní báze Knowledge Base (KB).

V editoru registru jsou verze rozhraní .NET Framework a nainstalované aktualizace pro jednotlivé verze uloženy v různých podklíčích. Informace o zjišťování čísla nainstalovaná verze najdete v tématu [postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Najít nainstalované aktualizace dotazováním registru v kódu

Následující příklad určuje prostřednictvím kódu programu rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix, které jsou nainstalovány v počítači:

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Tento příklad vytvoří výstupu, který je podobné následující:

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

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Najít nainstalované aktualizace dotazováním registru v prostředí PowerShell

Následující příklad ukazuje, jak určit rozhraní .NET Framework bezpečnostní aktualizace a opravy hotfix, které jsou nainstalovány v počítači pomocí prostředí PowerShell:

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

Tento příklad vytvoří výstupu, který je podobné následující:

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

[Postupy: zjištění nainstalovaných verzí rozhraní .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[Nainstalujte rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md)  
[Verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md)
