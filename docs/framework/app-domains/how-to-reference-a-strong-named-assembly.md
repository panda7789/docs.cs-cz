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
ms.openlocfilehash: 080d05a27b9e0b6ad4ff52d67ef8d9209dc1c697
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927958"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Postupy: Odkazování na sestavení se silným názvem
Proces pro odkazování na typy nebo prostředky v sestavení se silným názvem je obvykle transparentní. Odkaz lze vytvořit buď v době kompilace (počáteční vazba), nebo v době běhu.  
  
 K referenci v době kompilace dojde, když označíte kompilátor, který sestavení explicitně odkazuje na jiné sestavení. Použijete-li referenční informace při kompilaci, kompilátor automaticky získá veřejný klíč cílového sestavení se silným názvem a umístí jej do odkazu na sestavení zkompilovaného sestavení.  
  
> [!NOTE]
> Sestavení se silným názvem může používat pouze typy z jiných sestavení se silným názvem. V opačném případě by došlo k ohrožení zabezpečení sestavení se silným názvem.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Vytvoření odkazu na sestavení v čase kompilace na sestavení se silným názvem  
  
1. V příkazovém řádku zadejte následující příkaz:  
  
     \<*Kompilátor*>  **– příkaz/reference:** \<*název sestavení*>  
  
     V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk, který používáte, a *názvem sestavení* je název odkazovaného sestavení se silným názvem. Můžete také použít další možnosti kompilátoru, jako je například možnost **/t: Library** pro vytvoření sestavení knihovny.  
  
 Následující příklad vytvoří sestavení s názvem `myAssembly.dll` , které odkazuje na sestavení se silným názvem, které je voláno `myAssembly.cs` `myLibAssembly.dll` z modulu Code s názvem.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Chcete-li vytvořit odkaz na sestavení se silným názvem v době běhu  
  
1. Když vytvoříte odkaz na sestavení se silným názvem (například pomocí <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody nebo <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ), musíte použít zobrazovaný název odkazovaného sestavení se silným názvem. Syntaxe zobrazovaného názvu je následující:  
  
     \<*název* sestavení,\< *číslo verze,* *jazyková verze* , tokenveřejného\<klíče> \<>>>  
  
     Příklad:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     V tomto příkladu `PublicKeyToken` je hexadecimální forma tokenu veřejného klíče. Pokud není k dispozici žádná hodnota jazykové `Culture=neutral`verze, použijte.  
  
 Následující příklad kódu ukazuje, jak použít tyto informace s <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodou.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Můžete vytisknout hexadecimální formát veřejného klíče a tokenu veřejného klíče pro konkrétní sestavení pomocí následujícího příkazu [silného názvu (Sn. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) :  
  
 *sestavení* **sn- \< TP** **>**  
  
 Pokud máte soubor s veřejným klíčem, můžete místo toho použít následující příkaz (Poznamenejte si rozdíl v případě použití možnosti příkazového řádku):  
  
 *soubor veřejného klíče*  **\< SN-TP** **>**  
  
## <a name="see-also"></a>Viz také:

- [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
