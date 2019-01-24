---
title: 'Postupy: Nastavení entit jako serializovatelných'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 9b4ff81b4a779b474097de1a69e65f4864e08691
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604211"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="d6e8b-102">Postupy: Nastavení entit jako serializovatelných</span><span class="sxs-lookup"><span data-stu-id="d6e8b-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="d6e8b-103">Je možné nastavení entit jako serializovatelných při generování kódu.</span><span class="sxs-lookup"><span data-stu-id="d6e8b-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="d6e8b-104">Jsou vybaveny tříd entit <xref:System.Runtime.Serialization.DataContractAttribute> atribut a sloupce s <xref:System.Runtime.Serialization.DataMemberAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="d6e8b-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="d6e8b-105">Pomocí sady Visual Studio mohou vývojáři [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="d6e8b-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="d6e8b-106">Pokud používáte nástroj příkazového řádku SQLMetal, použijte **/serialization** spolu s možností `unidirectional` argument.</span><span class="sxs-lookup"><span data-stu-id="d6e8b-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="d6e8b-107">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d6e8b-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6e8b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6e8b-108">Example</span></span>  
 <span data-ttu-id="d6e8b-109">Následujících příkazových řádků SQLMetal vytvoří soubory, které se mají serializovat entity.</span><span class="sxs-lookup"><span data-stu-id="d6e8b-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6e8b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6e8b-110">See also</span></span>
- [<span data-ttu-id="d6e8b-111">Serializace</span><span class="sxs-lookup"><span data-stu-id="d6e8b-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [<span data-ttu-id="d6e8b-112">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="d6e8b-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
