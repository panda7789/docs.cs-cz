---
title: 'Postupy: vytváření entit serializovatelných'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 5e9d078ed2daacfa48b09693f533e9aade613281
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002707"
---
# <a name="how-to-make-entities-serializable"></a>Postupy: vytváření entit serializovatelných
Při generování kódu můžete označit entity jako serializovatelné. Třídy entit jsou upraveny pomocí atributu <xref:System.Runtime.Serialization.DataContractAttribute> a sloupce s atributem <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
 Vývojáři, kteří používají Visual Studio, mohou pro tento účel použít Návrhář relací objektů.  
  
 Pokud používáte nástroj příkazového řádku SQLMetal, použijte možnost **/Serialization** s argumentem `unidirectional`. Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Příklad  
 Následující příkazové řádky SQLMetal vytváří soubory s serializovatelnými entitami.  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Viz také:

- [Serializace](serialization.md)
- [Vytvoření objektového modelu](creating-the-object-model.md)
