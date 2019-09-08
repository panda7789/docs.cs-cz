---
title: Uživatelem definované funkce
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 40697da4fe678668f8f7ecda86abebf40da7b973
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792301"
---
# <a name="user-defined-functions"></a><span data-ttu-id="f13a3-102">Uživatelem definované funkce</span><span class="sxs-lookup"><span data-stu-id="f13a3-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f13a3-103">používá metody v objektovém modelu k reprezentaci uživatelsky definovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="f13a3-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="f13a3-104">Metody můžete určit jako funkce <xref:System.Data.Linq.Mapping.FunctionAttribute> použitím atributu a v případě potřeby <xref:System.Data.Linq.Mapping.ParameterAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="f13a3-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="f13a3-105">Další informace najdete v tématu [model objektu LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="f13a3-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="f13a3-106">Aby se zabránilo tomu <xref:System.InvalidOperationException>, uživatelsky definované funkce v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nástroji musí být v jednom z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="f13a3-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
- <span data-ttu-id="f13a3-107">Funkce zabalená jako volání metody se správnými atributy mapování.</span><span class="sxs-lookup"><span data-stu-id="f13a3-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="f13a3-108">Další informace najdete v tématu [mapování na základě atributů](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="f13a3-108">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="f13a3-109">Statická metoda SQL specifická pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f13a3-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
- <span data-ttu-id="f13a3-110">Funkce podporovaná metodou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f13a3-110">A function supported by a .NET Framework method.</span></span>  
  
 <span data-ttu-id="f13a3-111">Témata v této části ukazují, jak vytvořit a volat tyto metody v aplikaci, pokud píšete kód sami.</span><span class="sxs-lookup"><span data-stu-id="f13a3-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="f13a3-112">Vývojáři, kteří používají Visual Studio, by obvykle používali Návrhář relací objektů k mapování uživatelsky definovaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="f13a3-112">Developers using Visual Studio would typically use the Object Relational Designer to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f13a3-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f13a3-113">In This Section</span></span>  
 [<span data-ttu-id="f13a3-114">Postupy: Použití uživatelem definovaných funkcí s skalární hodnotou</span><span class="sxs-lookup"><span data-stu-id="f13a3-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="f13a3-115">Popisuje, jak implementovat funkci, která vrací skalární hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f13a3-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="f13a3-116">Postupy: Použití uživatelsky definovaných funkcí s hodnotou tabulky</span><span class="sxs-lookup"><span data-stu-id="f13a3-116">How to: Use Table-Valued User-Defined Functions</span></span>](how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="f13a3-117">Popisuje, jak implementovat funkci, která vrací hodnoty tabulky.</span><span class="sxs-lookup"><span data-stu-id="f13a3-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="f13a3-118">Postupy: Volání uživatelsky definovaných funkcí – inline</span><span class="sxs-lookup"><span data-stu-id="f13a3-118">How to: Call User-Defined Functions Inline</span></span>](how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="f13a3-119">Popisuje, jak provést vložená volání funkcí a rozdíly v provádění, když je volání provedeno jako vložené.</span><span class="sxs-lookup"><span data-stu-id="f13a3-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
