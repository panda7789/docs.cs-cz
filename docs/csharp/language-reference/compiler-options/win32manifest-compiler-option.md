---
title: -win32manifest (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924672"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (C# možnosti kompilátoru)
Pomocí možnosti **-win32manifest** určete uživatelsky definovaný soubor manifestu aplikace Win32, který bude vložen do přenositelného spustitelného souboru (PE) projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název a umístění vlastního souboru manifestu.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení vkládá vizuální C# kompilátor manifest aplikace, který určuje požadovanou úroveň spuštění "podle volajícího". Vytvoří manifest ve stejné složce, ve které je sestaven spustitelný soubor, obvykle složka bin\Debug nebo bin\Release při použití sady Visual Studio. Pokud chcete zadat vlastní manifest, například pro určení požadované úrovně spuštění "nejvyšší dostupná" nebo "vyžadovat správce", použijte tuto možnost k zadání názvu souboru.  
  
> [!NOTE]
> Tato možnost a možnost [-win32res (C# možnosti kompilátoru)](./win32res-compiler-option.md) se vzájemně vylučují. Pokud se pokusíte použít obě možnosti na stejném příkazovém řádku, zobrazí se chyba buildu.  
  
 Aplikace, která nemá žádný manifest aplikace, který určuje požadovanou úroveň spuštění, bude v rámci funkce řízení uživatelských účtů ve Windows podléhat virtualizaci File/Registry. Další informace najdete v tématu [řízení uživatelských účtů](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Vaše aplikace bude platit z virtualizace, pokud je splněna jedna z těchto podmínek:  
  
- Použijete možnost **-nowin32manifest** a neposkytnete manifest v pozdějším kroku sestavení nebo jako součást souboru prostředků Windows (. res) pomocí možnosti **-win32res** .  
  
- Poskytnete vlastní manifest, který neurčuje požadovanou úroveň spuštění.  
  
 Visual Studio vytvoří soubor default. manifest a uloží ho do adresářů pro ladění a vydání spolu se spustitelným souborem. Vlastní manifest můžete přidat tak, že ho vytvoříte v libovolném textovém editoru a pak ho přidáte do projektu. Případně můžete kliknout pravým tlačítkem myši na ikonu **projektu** v **Průzkumník řešení**, kliknout na **Přidat novou položku**a pak kliknout na **soubor manifestu aplikace**. Po přidání nového nebo existujícího souboru manifestu se zobrazí v rozevíracím seznamu **manifest** . Další informace naleznete na [stránce aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Manifest aplikace můžete zadat jako vlastní krok po sestavení nebo jako součást souboru prostředků Win32 pomocí možnosti [-nowin32manifest (C# možnosti kompilátoru)](./nowin32manifest-compiler-option.md) . Tuto možnost použijte, pokud chcete, aby se vaše aplikace mohla vztahovat k virtualizaci souborů nebo registru v systému Windows Vista. Tím zabráníte kompilátoru v vytváření a vkládání výchozího manifestu do přenositelného spustitelného souboru (PE).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje výchozí manifest, který Visual C# Compiler vloží do PE.  
  
> [!NOTE]
> Kompilátor vloží do XML standardní název aplikace "MyApplication. app". Toto je alternativní řešení pro povolení spouštění aplikací v systému Windows Server 2003 s aktualizací Service Pack 3.  
  
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

- [Možnosti kompilátoru jazyka C#](./index.md)
- [-nowin32manifest (C# možnosti kompilátoru)](./nowin32manifest-compiler-option.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
