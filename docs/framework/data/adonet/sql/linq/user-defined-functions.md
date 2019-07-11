---
title: Uživatelem definované funkce
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 54faca27e3f70283144f902e531e2a08e45bae3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742709"
---
# <a name="user-defined-functions"></a><span data-ttu-id="27e25-102">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="27e25-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="27e25-103">metody v objektovém modelu používá k reprezentaci uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="27e25-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="27e25-104">Označení metod jako funkce použitím <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="27e25-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="27e25-105">Další informace najdete v tématu [The LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="27e25-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="27e25-106">Aby se zabránilo <xref:System.InvalidOperationException>, uživatelem definované funkce v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí být v jednom z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="27e25-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="27e25-107">Zabalená funkce jako volání metody s atributy správné mapování.</span><span class="sxs-lookup"><span data-stu-id="27e25-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="27e25-108">Další informace najdete v tématu [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="27e25-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="27e25-109">Specifické pro statickou metodu SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27e25-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="27e25-110">Funkce nepodporuje metodu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27e25-110">A function supported by a .NET Framework method.</span></span>  
  
 <span data-ttu-id="27e25-111">Témata v této části ukazují, jak formulář a volat tyto metody ve své aplikaci psát kód sami.</span><span class="sxs-lookup"><span data-stu-id="27e25-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="27e25-112">Vývojářům používajícím Visual Studio by obvykle pomocí Návrháře relací objektů mapovat uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="27e25-112">Developers using Visual Studio would typically use the Object Relational Designer to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27e25-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="27e25-113">In This Section</span></span>  
 [<span data-ttu-id="27e25-114">Postupy: Použití funkce vracející skalární uživatelem definované</span><span class="sxs-lookup"><span data-stu-id="27e25-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="27e25-115">Popisuje, jak implementovat funkci vracející skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="27e25-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="27e25-116">Postupy: Použití Table-Valued uživatelsky definovaných funkcí</span><span class="sxs-lookup"><span data-stu-id="27e25-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="27e25-117">Popisuje, jak implementovat funkci vracející tabulku hodnot.</span><span class="sxs-lookup"><span data-stu-id="27e25-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="27e25-118">Postupy: Volat uživatelsky definovaných funkcí</span><span class="sxs-lookup"><span data-stu-id="27e25-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="27e25-119">Popisuje, jak volat vložené funkce a jaký je rozdíl v provádění po přišla vložené.</span><span class="sxs-lookup"><span data-stu-id="27e25-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
