---
title: 'Postupy: Přidání odkazů do knihoven typů'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c12096739e66a47fadd89eb27e30ba3de43c7da3
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836432"
---
# <a name="how-to-add-references-to-type-libraries"></a>Postupy: Přidání odkazů do knihoven typů
Visual Studio vytvoří definiční sestavení obsahující metadata, když přidáte odkaz na knihovnu typů. Pokud je k dispozici primární sestavení zprostředkovatele komunikace, Visual Studio používá existující sestavení před generováním nového sestavení zprostředkovatele komunikace.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Chcete-li přidat odkaz na knihovnu typů v sadě Visual Studio  
  
1.  Instalace knihovny COM DLL nebo EXE soubor v počítači, není-li soubor Windows Setup.exe provede instalaci za vás.  
  
2.  Zvolte **projektu**, **přidat odkaz na**.  
  
3.  Vyberte ve Správci odkazů **COM**.  
  
4.  Vyberte knihovnu typů, ze seznamu nebo vyhledání souboru .tlb.  
  
5.  Zvolte **OK**.  
  
6.  V Průzkumníku řešení otevřete místní nabídku pro odkaz, který jste právě přidali a klikněte na tlačítko **vlastnosti**.  
  
7.  V **vlastnosti** okno, ujistěte se, že **Embed Interop Types** je nastavena na **True**. To způsobí, že Visual Studio pro vložení informací o typu pro typy modelu COM v spustitelné soubory, takže odpadá potřeba k nasazení primárních sestavení vzájemné spolupráce s vaší aplikací.  
  
> [!NOTE]
>  Pole možnosti nabídky a dialogové okno se mohou lišit v závislosti na verzi sady Visual Studio, kterou používáte.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Chcete-li přidat odkaz na knihovnu typů pro sestavení příkazového řádku  
  
1.  Generování sestavení vzájemné spolupráce, jak je popsáno v [jak: Generování sestavení vzájemné spolupráce z knihoven typů](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Použití [/link (C# – možnosti kompilátoru)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) – možnost kompilátoru s názvem sestavení vzájemné spolupráce pro vložení informací o typu pro model COM typy, které do vašeho spustitelné soubory.  
  
## <a name="see-also"></a>Viz také:
- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) 
- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [/ Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/ Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
