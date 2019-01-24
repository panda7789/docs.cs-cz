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
ms.openlocfilehash: 9718febfe5aefba75decc133ad2113b64e4547de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618074"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (možnosti kompilátoru C#)
Použití **-win32manifest** možnost určit uživatelský soubor manifestu aplikace Win32, který má být vložen do projektu soubor (PE portable executable).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název a umístění vlastního souboru manifestu.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení kompilátor Visual C# vloží manifest aplikace, který určuje požadovanou úroveň spuštění "asInvoker". Manifest vytvoří ve stejné složce, ve kterém spustitelný soubor vytvořen, obvykle bin\Debug nebo bin\Release složky, pokud používáte sadu Visual Studio. Pokud chcete zadat vlastní manifest, třeba když chcete požadovanou úroveň spuštění "highestAvailable" nebo "requireAdministrator", zadejte tuto možnost použijte k zadání názvu souboru.  
  
> [!NOTE]
>  Tuto možnost a [-win32res (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) možnost se vzájemně vylučují. Pokud se pokusíte použít obě možnosti jsou ve stejném příkazovém řádku se zobrazí chybu sestavení.  
  
 Aplikace nemá žádné aplikace, manifest, který určuje, že že požadovanou úroveň spuštění bude v souladu s virtualizací souborů nebo registru pod funkci Řízení uživatelských účtů ve Windows. Další informace najdete v tématu [řízení uživatelských účtů](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Vaše aplikace bude v souladu s virtualizace, pokud platí některá z těchto podmínek:  
  
-   Použijete **-nowin32manifest** a neposkytuje manifest v pozdějším kroku sestavení nebo jako součást souboru prostředků (.res) Windows s použitím **-win32res** možnost.  
  
-   Poskytnete vlastního manifestu, která neurčuje požadovanou úroveň spuštění.  
  
 Visual Studio vytvoří výchozí soubor .manifest a ukládá ho do adresáře debug a release spustitelný soubor. Vytvoření nového v libovolném textovém editoru a následným přidáním souboru do projektu můžete přidat vlastní manifest. Alternativně je můžete kliknout pravým tlačítkem **projektu** ikonu **Průzkumníku řešení**, klikněte na tlačítko **přidat novou položku**a potom klikněte na tlačítko **soubor manifestu aplikace**. Po přidání nového nebo existujícího souboru manifestu, se zobrazí v **Manifest** rozevírací seznam. Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Manifest aplikace můžete zadat jako vlastní krok po sestavení nebo jako součást soubor prostředků Win32 pomocí [-nowin32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) možnost. Stejnou možnost použijte, pokud chcete, aby byla v souladu s virtualizací souborů nebo registru v systému Windows Vista aplikace. To zabrání kompilátoru od vytvoření a vkládání výchozí manifest do přenosného spustitelného souboru (PE).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje výchozí manifest, že kompilátor Visual C# vloží do PE.  
  
> [!NOTE]
>  Kompilátor vloží název standardní aplikace "MyApplication.app" do souboru xml. Toto je alternativní řešení Chcete-li povolit aplikace, které poběží na Windows Server 2003 Service Pack 3.  
  
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

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [-nowin32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
