---
title: 'Postupy: Přidávání odkazů do knihoven typů'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03c05e7399e9378751f803ae56dfaf664490e6d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-references-to-type-libraries"></a>Postupy: Přidávání odkazů do knihoven typů
Visual Studio generuje spolupráce sestavení obsahující metadata, když přidáte odkaz na knihovnu typů. Pokud je primární spolupracující sestavení je k dispozici, Visual Studio použije existující sestavení před vygenerováním nové sestavení vzájemné spolupráce.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Chcete-li přidat odkaz na knihovnu typů v sadě Visual Studio  
  
1.  Nainstalujte soubor COM DLL nebo EXE v počítači, pokud soubor Setup.exe systému Windows pro vás provede instalaci.  
  
2.  Zvolte **projektu**, **přidat odkaz**.  
  
3.  Zvolte ve Správci odkaz **COM**.  
  
4.  Vyberte typ knihovnu ze seznamu nebo .tlb soubor vyhledejte.  
  
5.  Zvolte **OK**.  
  
6.  V Průzkumníku řešení otevřete místní nabídku pro odkaz, na které jste právě přidali a potom zvolte **vlastnosti**.  
  
7.  V **vlastnosti** okna, ujistěte se, že **vložit zprostředkovatel komunikace s objekty typy** je nastavena na **True**. To způsobí, že Visual Studio pro vložení informací o typu pro typy modelu COM v spustitelné soubory, takže není nutné nasadit primárních sestavení vzájemné spolupráce s vaší aplikací.  
  
> [!NOTE]
>  Nabídce a dialogové okno Možnosti se může lišit v závislosti na verzi Visual Studia, kterou používáte.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Chcete-li přidat odkaz na knihovnu typů pro příkazového řádku kompilace  
  
1.  Generování sestavení vzájemné spolupráce, jak je popsáno v [postupy: generování sestavení zprostředkovatel komunikace s objekty z knihoven typů](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Použití [/Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) – možnost kompilátoru s názvem sestavení vzájemné spolupráce pro vložení informací o typu pro model COM typy, které do vašeho spustitelné soubory.  
  
## <a name="see-also"></a>Viz také  
 [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)  
 [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)  
 [Návod: Vložení informací o typu ze sestavení Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))  
 [Návod: Vložení typů ze spravovaných sestavení](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [/ Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [/ Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
