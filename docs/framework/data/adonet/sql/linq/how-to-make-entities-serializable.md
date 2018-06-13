---
title: 'Postupy: Zkontrolujte serializovatelný entity'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: c3b877df9707e0f98dbc2238d910842649def07f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354943"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="995df-102">Postupy: Zkontrolujte serializovatelný entity</span><span class="sxs-lookup"><span data-stu-id="995df-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="995df-103">Při generování kódu, můžete provést entity serializable.</span><span class="sxs-lookup"><span data-stu-id="995df-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="995df-104">Třídy entity jsou označených pomocí <xref:System.Runtime.Serialization.DataContractAttribute> atribut a sloupce s <xref:System.Runtime.Serialization.DataMemberAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="995df-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="995df-105">Vývojáři pomocí sady Visual Studio můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="995df-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="995df-106">Pokud používáte nástroj příkazového řádku na SQLMetal, použijte **/serialization** možnost s `unidirectional` argument.</span><span class="sxs-lookup"><span data-stu-id="995df-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="995df-107">Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="995df-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="995df-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="995df-108">Example</span></span>  
 <span data-ttu-id="995df-109">Na příkazovém řádku následující SQLMetal vytvářet soubory, které mají serializovatelný entity.</span><span class="sxs-lookup"><span data-stu-id="995df-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="995df-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="995df-110">See Also</span></span>  
 [<span data-ttu-id="995df-111">Serializace</span><span class="sxs-lookup"><span data-stu-id="995df-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)  
 [<span data-ttu-id="995df-112">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="995df-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
