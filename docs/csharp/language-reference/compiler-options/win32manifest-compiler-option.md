---
title: -win32manifest (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924672"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (Možnosti kompilátoru Jazyka C#)
Pomocí možnosti **-win32manifest** určete uživatelem definovaný soubor manifestu aplikace Win32, který má být vložen do přenosného spustitelného souboru projektu (PE).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Název a umístění vlastního souboru manifestu.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení kompilátor Visual C# vloží manifest aplikace, který určuje požadovanou úroveň spuštění "asInvoker". Vytvoří manifest ve stejné složce, ve které je vytvořen spustitelný soubor, obvykle bin\Debug nebo bin\Release folder při použití sady Visual Studio. Pokud chcete zadat vlastní manifest, například určit požadovanou úroveň spuštění "highestAvailable" nebo "requireAdministrator", použijte tuto možnost k určení názvu souboru.  
  
> [!NOTE]
> Tato možnost a [-win32res (C# Kompilátor možnosti)](./win32res-compiler-option.md) možnost se vzájemně vylučují. Pokud se pokusíte použít obě možnosti ve stejném příkazovém řádku, zobrazí se chyba sestavení.  
  
 Aplikace, která nemá žádný manifest aplikace, který určuje požadovanou úroveň spuštění, bude podléhat virtualizaci souborů a registru v rámci funkce Řízení uživatelských účtů v systému Windows. Další informace naleznete [v tématu Řízení uživatelských účtů](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Vaše aplikace bude podléhat virtualizaci, pokud je splněna některá z těchto podmínek:  
  
- Použijete **-nowin32manifest** možnost a neposkytují manifest v kroku pozdější sestavení nebo jako součást souboru Windows Resource (.res) pomocí **-win32res** možnost.  
  
- Zadáte vlastní manifest, který neurčuje požadovanou úroveň spuštění.  
  
 Visual Studio vytvoří výchozí soubor manifestu a uloží jej do ladicích a uvolňovacích adresářů vedle spustitelného souboru. Vlastní manifest můžete přidat tak, že jej vytvoříte v libovolném textovém editoru a potom přidáte soubor do projektu. Případně můžete v **Průzkumníkovi řešení**klepnout pravým tlačítkem myši na ikonu **Projekt** , kliknout na **Přidat novou položku**a potom kliknout na soubor **manifestu aplikace**. Po přidání nového nebo existujícího souboru manifestu se zobrazí v rozevíracím seznamu **Manifest.** Další informace naleznete v [tématu Stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Manifest aplikace můžete zadat jako vlastní krok po sestavení nebo jako součást souboru prostředků Win32 pomocí možnosti [-nowin32manifest (C# Compiler Options).](./nowin32manifest-compiler-option.md) Stejnou možnost použijte, pokud chcete, aby vaše aplikace podléhala virtualizaci souborů nebo registru v systému Windows Vista. Tím zabráníte kompilátoru ve vytváření a vkládání výchozího manifestu do přenosného spustitelného souboru (PE).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje výchozí manifest, který kompilátor Visual C# vloží do PE.  
  
> [!NOTE]
> Kompilátor vloží do xml standardní název aplikace MyApplication.app. Toto řešení umožňuje spuštění aplikací v systému Windows Server 2003 Service Pack 3.  
  
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
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [-nowin32manifest (Možnosti kompilátoru Jazyka C#)](./nowin32manifest-compiler-option.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
