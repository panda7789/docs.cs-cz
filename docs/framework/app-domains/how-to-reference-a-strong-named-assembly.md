---
title: "Postupy: Odkazování na sestavení se silným názvem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b005926f99b7c151e5916a95a9852dd8b448a928
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Postupy: Odkazování na sestavení se silným názvem
Proces pro odkazování na typy nebo prostředky v sestavení se silným názvem je obvykle transparentní. Odkaz můžete provést v době kompilace (časné vazby) nebo za běhu.  
  
 Odkaz kompilaci nastane, když kompilátoru určujete, že vaše sestavení výslovně odkazuje na jiné sestavení. Použijete-li odkazující na kompilaci, kompilátor automaticky získá veřejný klíč cílové sestavení se silným názvem a umístí ji do odkaz na sestavení právě kompilované sestavení.  
  
> [!NOTE]
>  Sestavení se silným názvem lze použít pouze typy od ostatních sestavení se silným názvem. Jinak by dojít k ohrožení zabezpečení sestavení se silným názvem.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Chcete-li kompilaci odkaz na sestavení se silným názvem  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     \<*příkaz kompilátoru*> **/reference:**\<*název sestavení*>  
  
     V tomto příkazu *kompilátoru příkaz* je příkaz kompilátoru pro jazyk, který používáte, a *název sestavení* je název sestavení se silným názvem, se na ně odkazovat. Můžete také použít jiné možnosti kompilátoru, jako **/t:library** možnost pro vytvoření sestavení knihovny.  
  
 Následující příklad vytvoří sestavení nazvané `myAssembly.dll` odkazující sestavení se silným názvem názvem `myLibAssembly.dll` z modulu kódu názvem `myAssembly.cs`.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Chcete-li spuštění odkaz na sestavení se silným názvem  
  
1.  Pokud provedete spuštění odkaz na sestavení se silným názvem (například pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> metoda), musíte použít zobrazovaný název odkazovaného sestavení se silným názvem. Syntaxe názvu zobrazení je následující:  
  
     \<*název sestavení*>**,** \< *číslo verze*>**,** \<  *jazyková verze*>**,** \< *tokenu veřejného klíče*>  
  
     Příklad:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     V tomto příkladu `PublicKeyToken` hexadecimální formu token veřejného klíče. Pokud není žádná hodnota jazykové verze, použijte `Culture=neutral`.  
  
 Následující příklad kódu ukazuje, jak používat tyto informace se <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Pomocí následujícího můžete vytisknout šestnáctkovém formátu veřejný klíč a tokenu veřejného klíče pro konkrétní sestavení [silného názvu (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) příkaz:  
  
 **sn - Tp \<**  *sestavení***>**  
  
 Pokud máte soubor veřejného klíče, můžete použít následující příkaz místo (Všimněte si rozdíl v případě na tuto možnost příkazového řádku):  
  
 **sn - tp \<**  *sestavení***>**  
  
## <a name="see-also"></a>Viz také  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
