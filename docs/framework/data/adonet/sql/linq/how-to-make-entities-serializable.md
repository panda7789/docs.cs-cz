---
title: 'Postupy: Nastavení entit jako serializovatelných'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: bbe40ec448bef5f62d4182d96f82c6308639e27f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086764"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="96d60-102">Postupy: Nastavení entit jako serializovatelných</span><span class="sxs-lookup"><span data-stu-id="96d60-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="96d60-103">Je možné nastavení entit jako serializovatelných při generování kódu.</span><span class="sxs-lookup"><span data-stu-id="96d60-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="96d60-104">Jsou vybaveny tříd entit <xref:System.Runtime.Serialization.DataContractAttribute> atribut a sloupce s <xref:System.Runtime.Serialization.DataMemberAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="96d60-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="96d60-105">Pomocí sady Visual Studio mohou vývojáři [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="96d60-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for this purpose.</span></span>  
  
 <span data-ttu-id="96d60-106">Pokud používáte nástroj příkazového řádku SQLMetal, použijte **/serialization** spolu s možností `unidirectional` argument.</span><span class="sxs-lookup"><span data-stu-id="96d60-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="96d60-107">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="96d60-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96d60-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="96d60-108">Example</span></span>  
 <span data-ttu-id="96d60-109">Následujících příkazových řádků SQLMetal vytvoří soubory, které se mají serializovat entity.</span><span class="sxs-lookup"><span data-stu-id="96d60-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="96d60-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96d60-110">See also</span></span>

- [<span data-ttu-id="96d60-111">Serializace</span><span class="sxs-lookup"><span data-stu-id="96d60-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [<span data-ttu-id="96d60-112">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="96d60-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
