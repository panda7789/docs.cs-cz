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
ms.openlocfilehash: 4f0f254b7794ce1cd4c765bee70c78e3c60a14aa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946498"
---
# <a name="how-to-add-references-to-type-libraries"></a>Postupy: Přidávání odkazů do knihoven typů
Když přidáte odkaz na knihovnu typů, Visual Studio vygeneruje sestavení vzájemné spolupráce obsahující metadata. Pokud je k dispozici primární sestavení vzájemné spolupráce, Visual Studio použije existující sestavení před generováním nového definičního sestavení.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Přidání odkazu na knihovnu typů v aplikaci Visual Studio  
  
1. Nainstalujte do počítače soubor DLL nebo EXE knihovny COM, pokud soubor instalační program systému Windows. exe instalaci neprovede.  
  
2. Vyberte **projekt**, **Přidat odkaz**.  
  
3. Ve Správci odkazů vyberte **com**.  
  
4. V seznamu vyberte knihovnu typů nebo vyhledejte soubor. tlb.  
  
5. Zvolte **OK**.  
  
6. V Průzkumník řešení otevřete místní nabídku pro odkaz, který jste právě přidali, a pak zvolte **vlastnosti**.  
  
7. V okně **vlastnosti** se ujistěte, že je vlastnost **Embed Interop Types** nastavená na **hodnotu true**. To způsobí, že Visual Studio vloží do vašich spustitelných souborů informace o typu modelu COM, což eliminuje nutnost nasazení primárních sestavení vzájemné spolupráce s vaší aplikací.  
  
> [!NOTE]
> Možnosti nabídky a dialogového okna se můžou lišit v závislosti na verzi sady Visual Studio, kterou používáte.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Přidání odkazu na knihovnu typů pro kompilaci příkazového řádku  
  
1. Vygenerujte sestavení vzájemné spolupráce, jak [je popsáno v tématu Postupy: Vygenerujte sestavení vzájemné spolupráce z](how-to-generate-interop-assemblies-from-type-libraries.md)knihoven typů.  
  
2. K vložení informací o typu pro typy COM ve vašich spustitelných souborech použijte možnost kompilátoru [/Link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) s názvem sestavení spolupráce.  
  
## <a name="see-also"></a>Viz také:

- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
- [Návod: Vložení typů ze spravovaných sestavení v aplikaci Visual StudioC#()](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) 
- [Návod: Vložení typů ze spravovaných sestavení v aplikaci Visual Studio (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [/Link (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
