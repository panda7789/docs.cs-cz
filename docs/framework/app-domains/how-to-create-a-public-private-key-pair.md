---
title: "Postupy: vytvoření páru veřejného a privátního klíče RSA"
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
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a0d1f54b417a9752ae96e52f78d9df7d2d60cbec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-public-private-key-pair"></a>Postupy: vytvoření páru veřejného a privátního klíče RSA
Pro podepsání sestavení silným názvem, musíte mít pár veřejného a privátního klíče. Tento pár veřejného a soukromého kryptografické klíče se používá během kompilace k vytvoření sestavení se silným názvem. Můžete vytvořit pár klíčů pomocí [silný název – nástroj (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md). Soubory párů klíčů obvykle mají příponu .snk.  
  
> [!NOTE]
>  V [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], zahrnout stránky vlastností projektu C# a Visual Basic **podpisování** kartu, která umožňuje vybrat existující soubory klíčů nebo generování nových klíčů souborů bez použití Sn.exe. V jazyce Visual C++, můžete zadat umístění existujícího souboru s klíčem v **Upřesnit** stránka vlastností v **Linkeru** části **vlastnosti konfigurace** části **Stránky vlastností** okno. Použití <xref:System.Reflection.AssemblyKeyFileAttribute> atribut k identifikaci soubor klíče dvojice byl proveden zastaralé od verze [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].  
  
### <a name="to-create-a-key-pair"></a>Chcete-li vytvořit pár klíčů  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     **sn – k** \< *název souboru*>  
  
     V tomto příkazu *název souboru* je název výstupního souboru, který obsahuje pár klíčů.  
  
 Následující příklad vytvoří pár klíčů nazvaný `sgKey.snk`.  
  
```  
sn -k sgKey.snk  
```  
  
 Pokud máte v úmyslu zpoždění podepsání sestavení a řídit celý pár klíčů (což je pravděpodobně mimo testovací scénáře), můžete použít následující příkazy ke generování páru klíčů a potom z něj extrahujte veřejný klíč do samostatného souboru. Nejprve vytvořte dvojici klíčů:  
  
```  
sn -k keypair.snk  
```  
  
 V dalším kroku extrahovat veřejný klíč z tohoto páru klíčů a zkopírujte jej do samostatného souboru:  
  
```  
sn -p keypair.snk public.snk  
```  
  
 Po vytvoření páru klíčů, je nutné umístit tam, kde podepisování silným názvem můžete najít soubor.  
  
 Při podpisu sestavení se silným názvem, [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) hledá klíč souboru relativní k aktuálnímu adresáři a do výstupního adresáře. Pokud používáte kompilátory příkazového řádku, můžete jednoduše zkopírovat klíč k aktuálnímu adresáři obsahuje moduly kódu.  
  
 Pokud používáte starší verzi [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , nemá **podpisování** karta ve vlastnostech projektu je umístění souboru doporučené klíče adresář projektu s atributem souboru určeným následujícím způsobem:  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
## <a name="see-also"></a>Viz také  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
