---
title: 'Postupy: Nastavení entit jako serializovatelných'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: fd687ba5dce16baee063f1d3bb9521c6664988b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743286"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="b4ccb-102">Postupy: Nastavení entit jako serializovatelných</span><span class="sxs-lookup"><span data-stu-id="b4ccb-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="b4ccb-103">Je možné nastavení entit jako serializovatelných při generování kódu.</span><span class="sxs-lookup"><span data-stu-id="b4ccb-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="b4ccb-104">Jsou vybaveny tříd entit <xref:System.Runtime.Serialization.DataContractAttribute> atribut a sloupce s <xref:System.Runtime.Serialization.DataMemberAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="b4ccb-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="b4ccb-105">Vývojáři, kteří používají Visual Studio můžete použít Návrháře relací objektů pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="b4ccb-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="b4ccb-106">Pokud používáte nástroj příkazového řádku SQLMetal, použijte **/serialization** spolu s možností `unidirectional` argument.</span><span class="sxs-lookup"><span data-stu-id="b4ccb-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="b4ccb-107">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b4ccb-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4ccb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4ccb-108">Example</span></span>  
 <span data-ttu-id="b4ccb-109">Následujících příkazových řádků SQLMetal vytvoří soubory, které se mají serializovat entity.</span><span class="sxs-lookup"><span data-stu-id="b4ccb-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4ccb-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4ccb-110">See also</span></span>

- [<span data-ttu-id="b4ccb-111">Serializace</span><span class="sxs-lookup"><span data-stu-id="b4ccb-111">Serialization</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [<span data-ttu-id="b4ccb-112">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="b4ccb-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
