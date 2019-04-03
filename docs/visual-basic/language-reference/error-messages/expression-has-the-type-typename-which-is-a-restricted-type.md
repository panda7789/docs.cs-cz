---
title: Výraz má typ '<typename>', což je omezený typ a nelze jej používat pro přístup ke členům zděděným z typu 'Object' nebo 'ValueType'.
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 6d2edadc323994f7f25394321fb1aff18f7154c5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824270"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="b5f8d-102">Výraz má typ "\<typename >' který je omezený typ a nelze použít pro přístup ke členům zděděným z 'Object' nebo 'ValueType'</span><span class="sxs-lookup"><span data-stu-id="b5f8d-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>
<span data-ttu-id="b5f8d-103">Výraz je vyhodnocen jako typ, který nemůže být pevně určený modulem common language runtime (CLR), ale zpřístupňuje člen, který vyžaduje přetypování pomocí boxingu.</span><span class="sxs-lookup"><span data-stu-id="b5f8d-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="b5f8d-104">*Zabalení* odkazuje na zpracování potřebné pro převod na typ `Object` nebo v některých případech k <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="b5f8d-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="b5f8d-105">Modul common language runtime nelze například pole určité typy struktur <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, a <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="b5f8d-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="b5f8d-106">Tento výraz pokusí použít typ s omezeným přístupem k volání metody zděděné z <xref:System.Object> nebo <xref:System.ValueType>, jako například <xref:System.Object.GetHashCode%2A> nebo <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5f8d-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="b5f8d-107">Přístup k této metodě, Visual Basic Probíhá pokus o implicitní zabalení převod, který způsobí, že k této chybě.</span><span class="sxs-lookup"><span data-stu-id="b5f8d-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="b5f8d-108">**ID chyby:** BC31393</span><span class="sxs-lookup"><span data-stu-id="b5f8d-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5f8d-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b5f8d-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="b5f8d-110">Vyhledejte výraz, který se vyhodnotí zmiňovanou typu.</span><span class="sxs-lookup"><span data-stu-id="b5f8d-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="b5f8d-111">Vyhledejte část, které se pokusí o volání metody zděděné z <xref:System.Object> nebo <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="b5f8d-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="b5f8d-112">Přepište příkaz tak, aby se zabránilo volání metody.</span><span class="sxs-lookup"><span data-stu-id="b5f8d-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f8d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5f8d-113">See also</span></span>

- [<span data-ttu-id="b5f8d-114">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="b5f8d-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
