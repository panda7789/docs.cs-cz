---
title: -win32manifest (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 3ac2b60b5e638290ea7e17e539519e3a0d355c12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214955"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (možnosti kompilátoru C#)
Použití **-win32manifest** možnost zadat vlastní soubor manifestu aplikace Win32, který má být vložen do souboru projektu přenosné spustitelný soubor (PE).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název a umístění vlastního souboru manifestu.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení kompilátor Visual C# vloží manifest aplikace, která určuje požadovanou úroveň vykonávání jako "asInvoker". Manifest vytvoří ve stejné složce, ve kterém spustitelný soubor je vytvořen, obvykle bin\Debug nebo bin\Release složky při použití sady Visual Studio. Pokud chcete zadat vlastní manifest, např. Chcete-li určit požadovanou úroveň vykonávání "highestAvailable" nebo "requireAdministrator" pomocí této možnosti můžete zadat název souboru.  
  
> [!NOTE]
>  Tuto možnost a [-win32res (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) se vzájemně vylučují. Pokud se pokusíte použít obě možnosti ve stejném příkazovém řádku obdržíte chybu sestavení.  
  
 Aplikace, která nemá žádné aplikace, manifest, který určuje že požadovanou úroveň vykonávání budou platit virtualizaci souborů a registrů pod funkci Řízení uživatelských účtů v systému Windows. Další informace najdete v tématu [řízení uživatelských účtů](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Aplikace budou platit virtualizace, pokud platí některá z těchto podmínek:  
  
-   Použijete **-nowin32manifest** a neposkytuje manifest v pozdější fázi sestavování nebo jako součást souboru prostředků Windows (.res) pomocí **-win32res** možnost.  
  
-   Můžete zadat vlastní manifestu, který není uveden požadovanou úroveň vykonávání.  
  
 Visual Studio vytvoří výchozí soubor manifest a ukládá je v adresářích debug a release společně se spustitelným souborem. Můžete přidat vlastní manifest vytvořením v každém textovém editoru a následným přidáním do projektu. Alternativně můžete můžete kliknout pravým tlačítkem **projektu** ikonu v **Průzkumníku řešení**, klikněte na tlačítko **přidat novou položku**a pak klikněte na tlačítko **soubor manifestu aplikace**. Po přidání nového nebo existujícího souboru manifestu se zobrazí v **Manifest** rozevíracím seznamu. Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Manifest aplikace můžete poskytnout jako vlastní krok po sestavení nebo jako součást zdrojového souboru Win32 pomocí [-nowin32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) možnost. Stejnou možnost použijte, pokud má vaše aplikace podléhat souborů nebo registru virtualizace v systému Windows Vista. To zabrání kompilátoru z vytváření a vložení manifestu výchozí do přenosného spustitelného souboru (PE).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje výchozí manifest, že kompilátor Visual C# vloží do PE.  
  
> [!NOTE]
>  Kompilátor vloží standardní název aplikace "MyApplication.app" do souboru xml. Toto je alternativní řešení Chcete-li povolit aplikací pro spuštění na Windows Server 2003 Service Pack 3.  
  
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
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [-nowin32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
