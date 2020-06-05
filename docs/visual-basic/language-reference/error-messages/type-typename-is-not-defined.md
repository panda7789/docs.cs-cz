---
title: Typ '<typename>' není definován.
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 89e2d1d18b456c96f62d6b9ee1dd8dc9d41bf665
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386929"
---
# <a name="type-typename-is-not-defined"></a>Typ '\<typename>' není definován.
Příkaz provedl odkaz na typ, který nebyl definován. Můžete definovat typ v příkazu deklarace `Enum` , jako je,, `Structure` `Class` nebo `Interface` .  
  
 **ID chyby:** BC30002  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zajistěte, aby definice typu a jejich odkazy používaly stejný pravopis.  
  
- Ujistěte se, že je pro odkaz k dispozici definice typu. Například pokud je typ v jiném modulu a byl deklarován `Private` , přesuňte definici typu na odkazující modul nebo deklaraci `Public` .  
  
- Ujistěte se, že obor názvů tohoto typu není předefinován v rámci projektu. Pokud je, použijte `Global` klíčové slovo k úplnému zařazení názvu typu. Například pokud projekt definuje obor názvů s názvem `System` , <xref:System.Object?displayProperty=nameWithType> typ není k dispozici, pokud není plně kvalifikován pomocí `Global` klíčového slova: `Global.System.Object` .  
  
- Pokud je definován typ, ale knihovna objektů nebo knihovna typů, ve které je definována, není registrována v Visual Basic, klikněte na tlačítko **Přidat odkaz** v nabídce **projekt** a vyberte příslušnou knihovnu objektů nebo knihovnu typů.  
  
- Zajistěte, aby byl typ v sestavení, které je součástí cílového .NET Framework profilu. Další informace najdete v tématu [řešení potíží s chybami cílení .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Viz také

- [Obory názvů v jazyce Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [Enum – příkaz](../statements/enum-statement.md)
- [Structure – příkaz](../statements/structure-statement.md)
- [Class – příkaz](../statements/class-statement.md)
- [Interface – příkaz](../statements/interface-statement.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
