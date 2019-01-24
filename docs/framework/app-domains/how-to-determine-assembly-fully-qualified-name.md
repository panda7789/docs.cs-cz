---
title: 'Postupy: Určení sestavení&#39;s plně kvalifikovaný název'
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
ms.openlocfilehash: b7124271c0118800883d4beb68591f8591ac43dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520708"
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a>Postupy: Určení sestavení&#39;s plně kvalifikovaný název
Chcete-li zjistit plně kvalifikovaný název sestavení v globální mezipaměti sestavení, použijte Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)). Zobrazit [jak: Zobrazení obsahu globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
  
 Pro sestavení, které nejsou v globální mezipaměti sestavení, je možné získat plně kvalifikovaný název v několika způsoby: kód můžete použít k výstupu informací do konzoly nebo do proměnné, nebo můžete použít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)pro přezkoumání metadat sestavení, který obsahuje plně kvalifikovaný název.  
  
-   Pokud už je sestavení zavedeno aplikací, můžete načíst hodnotu <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost získat plně kvalifikovaný název. Tento přístup můžete použít, zda je sestavení v mezipaměti GAC. Příklad uvádí ukázku.  
  
-   Pokud znáte cesta systému souborů sestavení, můžete volat statickou (`Shared` v jazyce Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodu k získání plně kvalifikovaný název. Níže je jednoduchý příklad.  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   Můžete použít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pro přezkoumání metadat sestavení, který obsahuje plně kvalifikovaný název.  
  
 Další informace o nastavení atributů sestavení, jako je verze, jazykovou verzi a název sestavení najdete v tématu [nastavení atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md). Další informace o přiřazení sestavení silným názvem naleznete v tématu [vytvoření a použití sestavení](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak zobrazit plně kvalifikovaný název sestavení obsahující dané třídy do konzoly. Protože načte název sestavení, které aplikace byl již načten, není důležité, zda je sestavení v mezipaměti GAC.  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- [Názvy sestavení](../../../docs/framework/app-domains/assembly-names.md)
- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)
- [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
