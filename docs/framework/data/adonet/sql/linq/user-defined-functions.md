---
title: Uživatelem definované funkce
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: f1222d9332d365c9c3c6ca2aa28cbb48e92c04e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917656"
---
# <a name="user-defined-functions"></a><span data-ttu-id="0856b-102">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="0856b-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0856b-103">metody v objektovém modelu používá k reprezentaci uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="0856b-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="0856b-104">Označení metod jako funkce použitím <xref:System.Data.Linq.Mapping.FunctionAttribute> atribut a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="0856b-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="0856b-105">Další informace najdete v tématu [The LINQ to SQL objektový Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="0856b-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="0856b-106">Aby se zabránilo <xref:System.InvalidOperationException>, uživatelem definované funkce v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí být v jednom z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="0856b-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="0856b-107">Zabalená funkce jako volání metody s atributy správné mapování.</span><span class="sxs-lookup"><span data-stu-id="0856b-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="0856b-108">Další informace najdete v tématu [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0856b-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="0856b-109">Specifické pro statickou metodu SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0856b-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="0856b-110">Funkce podporované [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] metoda.</span><span class="sxs-lookup"><span data-stu-id="0856b-110">A function supported by a [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] method.</span></span>  
  
 <span data-ttu-id="0856b-111">Témata v této části ukazují, jak formulář a volat tyto metody ve své aplikaci psát kód sami.</span><span class="sxs-lookup"><span data-stu-id="0856b-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="0856b-112">Obvykle byste použili vývojářům používajícím Visual Studio [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapovat uživatelem definované funkce.</span><span class="sxs-lookup"><span data-stu-id="0856b-112">Developers using Visual Studio would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0856b-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0856b-113">In This Section</span></span>  
 [<span data-ttu-id="0856b-114">Postupy: Použití funkce vracející skalární uživatelem definované</span><span class="sxs-lookup"><span data-stu-id="0856b-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="0856b-115">Popisuje, jak implementovat funkci vracející skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0856b-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="0856b-116">Postupy: Použití Table-Valued uživatelsky definovaných funkcí</span><span class="sxs-lookup"><span data-stu-id="0856b-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="0856b-117">Popisuje, jak implementovat funkci vracející tabulku hodnot.</span><span class="sxs-lookup"><span data-stu-id="0856b-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="0856b-118">Postupy: Volat uživatelsky definovaných funkcí</span><span class="sxs-lookup"><span data-stu-id="0856b-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="0856b-119">Popisuje, jak volat vložené funkce a jaký je rozdíl v provádění po přišla vložené.</span><span class="sxs-lookup"><span data-stu-id="0856b-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
