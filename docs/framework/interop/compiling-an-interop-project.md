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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b9f0cd44e5ab9a33db4dd2ef52681f40ca54080
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835158"
---
# <a name="compiling-an-interop-project"></a>Kompilace projektu interoperability

Projektů spolupráce modelu COM, které odkazují na jeden nebo více sestavení, která obsahují importované typy modelu COM jsou kompilovány jako ostatní spravovaného projektu. Můžete odkazovat na sestavení vzájemné spolupráce ve vývojovém prostředí, jako je Visual Studio, nebo je můžete odkazovat, při použití příkazového řádku kompilátoru. V obou případech se pro kompilaci správně, definiční sestavení musí být ve stejném adresáři jako jiné soubory projektu.

 Existují dva způsoby, jak odkazovat na sestavení vzájemné spolupráce:

-   Vložené typy spolupráce: Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a Visual Studio 2010, můžete dát pokyn kompilátoru k vložení informací o typu ze sestavení vzájemné spolupráce do spustitelného souboru. Toto je doporučený postup.

-   Nasazení sestavení vzájemné spolupráce: Můžete vytvořit standardní odkaz na sestavení vzájemné spolupráce. V takovém případě musí být nasazeny sestavení zprostředkovatele komunikace s vaší aplikací.

 Rozdíly mezi tyto dva postupy jsou podrobně popsány v větší [typy modelu COM pomocí spravovaného kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).

 Vkládání typů spolupráce pomocí sady Visual Studio jsou popsané v článku [názorný postup: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), a [názorný postup: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).

 Chcete-li odkazovat na sestavení vzájemné spolupráce pomocí kompilátoru příkazového řádku a vložit informace o typu v vaše spustitelné soubory, použijte [/Link (možnosti kompilátoru C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) přepínače kompilátoru a Zadejte název sestavení vzájemné spolupráce.

> [!NOTE]
> Aplikace Visual C++ nelze vložit informace o typu, ale můžou spolupracovat s aplikací nebo doplňky, které provést.

 Chcete-li kompilovat aplikaci, která obsahuje primární sestavení zprostředkovatele komunikace při nasazení, použijte **/reference** přepínače kompilátoru a zadejte název sestavení vzájemné spolupráce.

## <a name="see-also"></a>Viz také:

- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../standard/language-independence-and-language-independent-components.md)
- [Používání typů modelu COM ve spravovaném kódu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)