---
title: Kompilace projektu interoperability
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
ms.openlocfilehash: 32102910ae674a97e941e1346a1898585f503527
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123674"
---
# <a name="compiling-an-interop-project"></a>Kompilace projektu interoperability

Projekty Interop modelu COM, které odkazují na jedno nebo více sestavení obsahujících importované typy modelu COM, jsou kompilovány stejným způsobem jako jakýkoli jiný spravovaný projekt. Můžete odkazovat na sestavení spolupráce ve vývojovém prostředí, jako je například Visual Studio, nebo na ně můžete odkazovat při použití kompilátoru příkazového řádku. V obou případech pro správné kompilování definičního sestavení musí být ve stejném adresáři jako jiné soubory projektu.

 Existují dva způsoby, jak odkazovat na definiční sestavení:

- Vložené typy spolupráce: počínaje .NET Framework 4 a Visual Studio 2010 můžete instruovat kompilátor, aby vložil informace o typu ze sestavení pro spolupráci do spustitelného souboru. Toto je doporučený postup.

- Nasazení definičních sestavení: můžete vytvořit standardní odkaz na definiční sestavení. V takovém případě musí být definiční sestavení nasazeno s vaší aplikací.

 Rozdíly mezi těmito dvěma technikami jsou podrobněji popsány v tématu [použití typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).

 Vkládání typů spolupráce pomocí sady Visual Studio je znázorněno v [návodu: Vložení typů ze spravovaných sestavení v aplikaci Visual Studio](../../standard/assembly/embed-types-visual-studio.md).

 Chcete-li odkazovat na definiční sestavení s kompilátorem příkazového řádku a vkládat informace o typu ve vašich spustitelných souborech, použijte přepínač [-Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo přepínač [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) a zadejte název sestavení vzájemné spolupráce.

> [!NOTE]
> Aplikace Visual C++ nemůžou vkládat informace o typu, ale můžou spolupracovat s aplikacemi nebo doplňky, které to dělají.

 Chcete-li zkompilovat aplikaci, která zahrnuje primární definiční sestavení při nasazení, použijte přepínač **/reference** Compiler a zadejte název definičního sestavení.

## <a name="see-also"></a>Viz také

- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../standard/language-independence-and-language-independent-components.md)
- [Použití typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio](../../standard/assembly/embed-types-visual-studio.md)
- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
