---
title: Kompilace projektu interoperability
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cffb812a357acead35a42328a123106da0731d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="compiling-an-interop-project"></a>Kompilace projektu interoperability
Projektů spolupráce COM, které odkazují na jeden nebo více sestavení obsahující importované typy modelu COM kompilovány jako ostatní spravovaný projekt. Sestavení spolupráce ve vývojovém prostředí, jako je například Visual Studio, můžete odkazovat, nebo můžete použít, je při použití příkazového řádku kompilátoru. V obou případech správně, kompilace sestavení vzájemné spolupráce musí být ve stejném adresáři jako ostatní soubory projektu.  
  
 Chcete-li sestavení vzájemné spolupráce dvěma způsoby:  
  
-   Vložené typy spolupráce: od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], můžete určit, aby kompilátoru pro vložení informací o typu ze sestavení spolupráce do spustitelného souboru. Toto je doporučený postup.  
  
-   Nasazení sestavení vzájemné spolupráce: můžete vytvořit standardní odkaz na sestavení spolupráce. V takovém případě musí být nasazený sestavení vzájemné spolupráce s vaší aplikací.  
  
 Rozdíly mezi tyto dva postupy jsou popsány podrobněji na [pomocí typy modelu COM v spravovaného kódu](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).  
  
 Vložení typů spolupráce pomocí sady Visual Studio je znázorněn v [návod: vložení informací o typu ze sestavení sady Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) a [návod: vložení typů ze spravovaných sestavení](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Odkazování na sestavení spolupráce s kompilátoru příkazového řádku a vložení informací o typu do vaší spustitelné soubory, použijte [/Link (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) nebo [/Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) přepínače kompilátoru a Zadejte název sestavení vzájemné spolupráce.  
  
> [!NOTE]
>  Visual C++ aplikace nelze vložit informace o typu, ale můžou spolupracovat s aplikacemi nebo doplňky, které provádějí.  
  
 Kompilace aplikace, která zahrnuje primárních sestavení vzájemné spolupráce při nasazení, použijte **/reference** přepínače kompilátoru a zadejte název sestavení vzájemné spolupráce.  
  
## <a name="see-also"></a>Viz také  
 [Vystavení komponent COM pro rozhraní .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 [Jazyková nezávislost a jazykově nezávislé komponenty](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [Použití typy modelu COM ve spravovaném kódu](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [Návod: Vložení informací o typu ze sestavení Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [Návod: Vložení typů ze spravovaných sestavení](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [Import knihovny typů ve formě sestavení](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
