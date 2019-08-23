---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: 6eb9d50a3ecd80acb0349f1ba315d9cf8ccc6dc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937240"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
Identifikuje uživatelsky definovaný soubor manifestu aplikace Win32, který bude vložen do přenositelného spustitelného souboru (PE) projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`fileName`|Cesta k souboru vlastního manifestu.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení vloží kompilátor Visual Basic manifest aplikace, který určuje požadovanou úroveň spuštění podle volajícího. Vytvoří manifest ve stejné složce, ve které je sestaven spustitelný soubor, obvykle složka bin\Debug nebo bin\Release při použití sady Visual Studio. Pokud chcete zadat vlastní manifest, například pro určení požadované úrovně spuštění nejvyšší dostupná nebo vyžadovat správce, použijte tuto možnost k zadání názvu souboru.  
  
> [!NOTE]
> Tato možnost a možnost [-Win32Resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) se vzájemně vylučují. Pokud se pokusíte použít obě možnosti na stejném příkazovém řádku, zobrazí se chyba buildu.  
  
 Aplikace, která nemá žádný manifest aplikace, který určuje požadovanou úroveň spuštění, bude podléhat virtualizaci souborů nebo registru v rámci funkce řízení uživatelských účtů v systému Windows Vista. Další informace o virtualizaci najdete v tématu [nasazení ClickOnce v systému Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Pokud je splněna některá z následujících podmínek, bude se aplikace vztahovat k virtualizaci:  
  
1. Použijete `-nowin32manifest` možnost a neposkytnete manifest v pozdějším kroku sestavení nebo jako součást souboru prostředků systému Windows (. res) `-win32resource` pomocí možnosti.  
  
2. Poskytnete vlastní manifest, který neurčuje požadovanou úroveň spuštění.  
  
 Visual Studio vytvoří soubor default. manifest a uloží ho do adresářů pro ladění a vydání spolu se spustitelným souborem. Výchozí soubor App. manifest můžete zobrazit nebo upravit kliknutím na **Zobrazit nastavení nástroje řízení uživatelských účtů** na kartě **aplikace** v Návrháři projektu. Další informace naleznete na [stránce aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Manifest aplikace můžete zadat jako vlastní krok po sestavení nebo jako součást souboru prostředků Win32 pomocí `-nowin32manifest` možnosti. Tuto možnost použijte, pokud chcete, aby se vaše aplikace mohla vztahovat k virtualizaci souborů nebo registru v systému Windows Vista. Tím zabráníte kompilátoru v vytvoření a vložení výchozího manifestu do souboru PE.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje výchozí manifest, který Visual Basic Kompilátor vloží do PE.  
  
> [!NOTE]
> Kompilátor vloží do souboru XML manifestu standardní název aplikace MyApplication. app. Toto je alternativní řešení pro povolení spouštění aplikací v systému Windows Server 2003 s aktualizací Service Pack 3.  
  
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

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
