---
title: 'Postupy: Zkontrolujte serializovatelný entity'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: c3b877df9707e0f98dbc2238d910842649def07f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-entities-serializable"></a>Postupy: Zkontrolujte serializovatelný entity
Při generování kódu, můžete provést entity serializable. Třídy entity jsou označených pomocí <xref:System.Runtime.Serialization.DataContractAttribute> atribut a sloupce s <xref:System.Runtime.Serialization.DataMemberAttribute> atribut.  
  
 Vývojáři pomocí sady Visual Studio můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pro tento účel.  
  
 Pokud používáte nástroj příkazového řádku na SQLMetal, použijte **/serialization** možnost s `unidirectional` argument. Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Příklad  
 Na příkazovém řádku následující SQLMetal vytvářet soubory, které mají serializovatelný entity.  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Viz také  
 [Serializace](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)  
 [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
