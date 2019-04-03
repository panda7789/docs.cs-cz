---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: bd9a708b99d11b90e47c3413bb0003ce2def13a1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833712"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
Určuje uživatelský soubor manifestu aplikace Win32, který má být vložen do projektu soubor (PE portable executable).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`fileName`|Cesta vlastního souboru manifestu.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení vloží kompilátor jazyka Visual Basic, která určuje požadovanou úroveň spuštění asInvoker manifestu aplikace. Manifest vytvoří ve stejné složce, ve kterém spustitelného souboru, který je sestaven, obvykle bin\Debug nebo bin\Release složky, pokud používáte sadu Visual Studio. Pokud chcete zadat vlastní manifest, třeba když chcete požadovanou úroveň spuštění highestAvailable nebo requireAdministrator, zadejte tuto možnost použijte k zadání názvu souboru.  
  
> [!NOTE]
>  Tuto možnost a [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) možnost se vzájemně vylučují. Pokud se pokusíte použít obě možnosti jsou ve stejném příkazovém řádku, zobrazí se chyba buildu.  
  
 Aplikace nemá žádné aplikace, manifest, který určuje, že že požadovanou úroveň spuštění bude v souladu s virtualizací souborů nebo registru pod funkci Řízení uživatelských účtů ve Windows Vista. Další informace o virtualizaci, naleznete v tématu [nasazení ClickOnce v systému Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Vaše aplikace bude v souladu s virtualizace, pokud je splněna jedna z následujících podmínek:  
  
1.  Můžete použít `-nowin32manifest` a neposkytuje manifest v pozdějším kroku sestavení nebo jako součást souboru prostředků (.res) Windows s použitím `-win32resource` možnost.  
  
2.  Poskytnete vlastního manifestu, která neurčuje požadovanou úroveň spuštění.  
  
 Visual Studio vytvoří výchozí soubor .manifest a ukládá ho do adresáře debug a release spustitelný soubor. Můžete zobrazit nebo upravit výchozí soubor app.manifest kliknutím **nastavení nástroje Řízení uživatelských účtů zobrazení** na **aplikace** kartě v Návrháři projektu. Další informace najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Manifest aplikace můžete zadat jako vlastní krok po sestavení nebo jako součást soubor prostředků Win32 pomocí `-nowin32manifest` možnost. Stejnou možnost použijte, pokud chcete, aby byla v souladu s virtualizací souborů nebo registru v systému Windows Vista aplikace. To zabrání kompilátoru od vytvoření a vložení výchozí manifest do souboru PE.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje výchozí manifest, že kompilátor jazyka Visual Basic vloží do PE.  
  
> [!NOTE]
>  Kompilátor vloží název standardní aplikace MyApplication.app do manifestu XML. Toto je alternativní řešení Chcete-li povolit aplikace, které poběží na Windows Server 2003 Service Pack 3.  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
