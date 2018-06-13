---
title: 'Postupy: určení sestavení&#39;s plně kvalifikovaný název'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 663e7456337a2d9c413b15236e7ba1de33fbfa9b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743183"
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a>Postupy: určení sestavení&#39;s plně kvalifikovaný název
Chcete-li zjistit, plně kvalifikovaný název sestavení v globální mezipaměti sestavení, použijte nástroj globální mezipaměti sestavení ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)). V tématu [postupy: zobrazení obsahu globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
  
 Pro sestavení, které nejsou v globální mezipaměti sestavení, můžete získat plně kvalifikovaný název sestavení v mnoha různými způsoby: můžete použít kód pro výstup informací na konzole nebo proměnné, nebo můžete použít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)prozkoumat metadat sestavení, který obsahuje plně kvalifikovaný název.  
  
-   Pokud už je načtený sestavení aplikací, můžete načíst hodnotu <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost k získání plně kvalifikovaný název. Tento postup můžete použít, zda je sestavení v mezipaměti GAC. Příklad uvádí ukázku.  
  
-   Pokud znáte cesta systému souborů je sestavení, můžete volat statické (`Shared` v jazyce Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metoda získat plně kvalifikovaný název. Zde je jednoduchý příklad.  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   Můžete použít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) prozkoumat metadat sestavení, který obsahuje plně kvalifikovaný název.  
  
 Další informace o nastavení atributů sestavení například verze, jazykové verze a název sestavení najdete v tématu [nastavení atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md). Další informace o přiřazení sestavení silným názvem naleznete v tématu [vytvoření a použití sestavení](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak zobrazit plně kvalifikovaný název sestavení obsahující zadanou třídu do konzoly. Vzhledem k tomu, že ho načte název sestavení, které již načtena aplikace, není důležité, zda je sestavení v mezipaměti GAC.  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Názvy sestavení](../../../docs/framework/app-domains/assembly-names.md)  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
