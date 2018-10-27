---
title: 'Postupy: Odkazování na sestavení se silným názvem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18844a9e8eff574d061b044bf88bc7857ce8033e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182980"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Postupy: Odkazování na sestavení se silným názvem
Proces pro odkazování na typy a prostředky v sestavení se silným názvem je obvykle transparentní. Odkaz můžete provést v době kompilace (časné vazby) nebo v době běhu.  
  
 Kompilace odkaz nastane, pokud kompilátoru určujete, že vaše sestavení explicitně odkazuje na jiné sestavení. Při použití odkazující na kompilaci kompilátor automaticky získá veřejný klíč cílové sestavení se silným názvem a umístí jej v odkazu na sestavení kompiluje sestavení.  
  
> [!NOTE]
>  Sestavení se silným názvem lze použít pouze typy z jiných sestavení se silným názvem. V opačném případě by dojít k ohrožení zabezpečení sestavení se silným názvem.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Chcete-li kompilaci odkaz na sestavení se silným názvem  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     \<*příkaz kompilátoru*> **/reference:**\<*název sestavení*>  
  
     V tomto příkazu *kompilátoru příkaz* je příkaz kompilátoru pro jazyk používáte, a *název sestavení* je název sestavení se silným názvem, který se odkazuje. Můžete také použít jiné možnosti kompilátoru, jako **/t:library** volba pro vytvoření sestavení knihovny.  
  
 Následující příklad vytvoří sestavení nazvané `myAssembly.dll` , která odkazuje na sestavení se silným názvem se nazývá `myLibAssembly.dll` z modulu kódu volá `myAssembly.cs`.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Chcete-li za běhu odkaz na sestavení se silným názvem  
  
1.  Když nastavíte za běhu odkaz na sestavení se silným názvem (například pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> metoda), musíte použít zobrazovaný název odkazovaného sestavení se silným názvem. Název zobrazení syntaxe vypadá takto:  
  
     \<*název sestavení*>**,** \< *číslo verze*>**,** \< *jazykovou verzi*  > **,** \< *token veřejného klíče*>  
  
     Příklad:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     V tomto příkladu `PublicKeyToken` je šestnáctkovém formátu token veřejného klíče. Pokud není žádná hodnota jazykové verze, použít `Culture=neutral`.  
  
 Následující příklad kódu ukazuje, jak pomocí těchto informací s <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Můžete vytisknout šestnáctkovém formátu veřejný klíč a token veřejného klíče pro konkrétní sestavení pomocí následujících [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) příkaz:  
  
 **sériové číslo - Tp \<**  *sestavení* **>**  
  
 Pokud máte soubor veřejného klíče, můžete použít následující příkaz místo (Všimněte si rozdílů v případě na tuto možnost příkazového řádku):  
  
 **sériové číslo - tp \<**  *souboru veřejného klíče* **>**  
  
## <a name="see-also"></a>Viz také  
- [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
