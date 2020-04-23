---
title: 'Postupy: Přidávání odkazů do knihoven typů'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: 1e82a499b77cc6d1d49eaf13e243201bbdc4c5fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181435"
---
# <a name="how-to-add-references-to-type-libraries"></a>Postupy: Přidávání odkazů do knihoven typů
Když přidáte odkaz na knihovnu typů, Visual Studio vygeneruje sestavení vzájemné spolupráce obsahující metadata. Pokud je k dispozici primární sestavení vzájemné spolupráce, Visual Studio použije existující sestavení před generováním nového definičního sestavení.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Přidání odkazu na knihovnu typů v aplikaci Visual Studio  
  
1. Nainstalujte do počítače soubor DLL nebo EXE knihovny COM, pokud soubor instalační program systému Windows. exe instalaci neprovede.  
  
2. Vyberte **projekt**, **Přidat odkaz**.  
  
3. Ve Správci odkazů vyberte **com**.  
  
4. V seznamu vyberte knihovnu typů nebo vyhledejte soubor. tlb.  
  
5. Vyberte **OK**.  
  
6. V Průzkumník řešení otevřete místní nabídku pro odkaz, který jste právě přidali, a pak zvolte **vlastnosti**.  
  
7. V okně **vlastnosti** se ujistěte, že je vlastnost **Embed Interop Types** nastavená na **hodnotu true**. To způsobí, že Visual Studio vloží do vašich spustitelných souborů informace o typu modelu COM, což eliminuje nutnost nasazení primárních sestavení vzájemné spolupráce s vaší aplikací.  
  
> [!NOTE]
> Možnosti nabídky a dialogového okna se můžou lišit v závislosti na verzi sady Visual Studio, kterou používáte.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Přidání odkazu na knihovnu typů pro kompilaci příkazového řádku  
  
1. Vygenerujte sestavení vzájemné spolupráce, jak je popsáno v tématu [Postupy: generování sestavení vzájemné spolupráce z knihoven typů](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2. Použijte možnost [-Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) s názvem definičního sestavení pro vložení informací o typu pro typy com ve vašich spustitelných souborech.  
  
## <a name="see-also"></a>Viz také

- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio](../../standard/assembly/embed-types-visual-studio.md)
- [-Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
