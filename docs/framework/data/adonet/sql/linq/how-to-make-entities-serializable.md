---
title: 'Postupy: Nastavení entit jako serializovatelných'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 40a0b4d5a49f88af1bedcbefdd117f6c000b791d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793564"
---
# <a name="how-to-make-entities-serializable"></a>Postupy: Nastavení entit jako serializovatelných
Při generování kódu můžete označit entity jako serializovatelné. Třídy entit jsou upraveny <xref:System.Runtime.Serialization.DataContractAttribute> atributem a sloupcem <xref:System.Runtime.Serialization.DataMemberAttribute> s atributem.  
  
 Vývojáři, kteří používají Visual Studio, mohou pro tento účel použít Návrhář relací objektů.  
  
 Pokud používáte nástroj příkazového řádku SQLMetal, použijte možnost **/Serialization** s `unidirectional` argumentem. Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Příklad  
 Následující příkazové řádky SQLMetal vytváří soubory s serializovatelnými entitami.  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Viz také:

- [Serializace](serialization.md)
- [Vytvoření objektového modelu](creating-the-object-model.md)
