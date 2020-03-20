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
Visual Studio generuje interop sestavení obsahující metadata při přidání odkazu do knihovny typů. Pokud je k dispozici primární sestavení interop, Visual Studio používá existující sestavení před generováním nové ho sestavení interop.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Přidání odkazu na knihovnu typů v sadě Visual Studio  
  
1. Nainstalujte do počítače soubor COM DLL nebo EXE, pokud instalaci neprovede soubor Setup.exe systému Windows.  
  
2. Zvolte **Projekt**, **Přidat odkaz**.  
  
3. Ve Správci odkazů zvolte **COM**.  
  
4. Vyberte knihovnu typů ze seznamu nebo vyhledejte soubor TLB.  
  
5. Vyberte **OK**.  
  
6. V Průzkumníku řešení otevřete místní nabídku pro odkaz, který jste právě přidali, a pak zvolte **Vlastnosti**.  
  
7. V okně **Vlastnosti** zkontrolujte, zda je vlastnost **Embed Interop Types** nastavena na **hodnotu True**. To způsobí, že Visual Studio vložit informace o typu pro typy COM ve vašich spustitelných souborech, což eliminuje potřebu nasadit primární sestavení interop s vaší aplikací.  
  
> [!NOTE]
> Možnosti nabídky a dialogového okna se mohou lišit v závislosti na verzi sady Visual Studio, kterou používáte.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Přidání odkazu do knihovny typů pro kompilaci příkazového řádku  
  
1. Generovat sestavení interop, jak je popsáno v [postupech: Generovat interop sestavení z knihoven typů](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2. Pomocí možnosti kompilátoru [-link (C# Compiler)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) s názvem sestavení interop můžete vložit informace o typu pro typy COM do spustitelných souborů.  
  
## <a name="see-also"></a>Viz také

- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio](../../standard/assembly/embed-types-visual-studio.md)
- [-link (Možnosti kompilátoru Jazyka C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
