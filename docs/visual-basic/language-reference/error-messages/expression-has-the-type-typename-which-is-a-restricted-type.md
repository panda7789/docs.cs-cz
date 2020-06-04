---
title: Výraz má typ '<typename>', což je omezený typ a nelze jej používat pro přístup ke členům zděděným z typu 'Object' nebo 'ValueType'.
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 0eb30488312cc7519f39a6b819aea15489f2f70a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409517"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="02a85-102">Výraz má typ '\<typename>', což je omezený typ a nelze jej používat pro přístup ke členům zděděným z typu 'Object' nebo 'ValueType'.</span><span class="sxs-lookup"><span data-stu-id="02a85-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>
<span data-ttu-id="02a85-103">Výraz je vyhodnocen jako typ, který nemůže být zabalen modulem CLR (Common Language Runtime), ale přistupuje ke členu, který vyžaduje zabalení.</span><span class="sxs-lookup"><span data-stu-id="02a85-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="02a85-104">*Zabalení* odkazuje na zpracování potřebné k převedení typu na `Object` nebo, v některých případech na <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="02a85-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="02a85-105">Modul common language runtime nemůže určit určité typy struktury, například <xref:System.ArgIterator> <xref:System.RuntimeArgumentHandle> , a <xref:System.TypedReference> .</span><span class="sxs-lookup"><span data-stu-id="02a85-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="02a85-106">Tento výraz se pokusí použít typ s omezením pro volání metody zděděné z <xref:System.Object> nebo <xref:System.ValueType> , například <xref:System.Object.GetHashCode%2A> nebo <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="02a85-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="02a85-107">Pro přístup k této metodě Visual Basic došlo k pokusu o implicitní převod zabalení, který tuto chybu způsobuje.</span><span class="sxs-lookup"><span data-stu-id="02a85-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="02a85-108">**ID chyby:** BC31393</span><span class="sxs-lookup"><span data-stu-id="02a85-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02a85-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="02a85-109">To correct this error</span></span>  
  
1. <span data-ttu-id="02a85-110">Vyhledejte výraz, který se vyhodnotí na citovaný typ.</span><span class="sxs-lookup"><span data-stu-id="02a85-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2. <span data-ttu-id="02a85-111">Vyhledejte část příkazu, která se pokusí zavolat metodu zděděnou z <xref:System.Object> nebo <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="02a85-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3. <span data-ttu-id="02a85-112">Přepište příkaz, aby se zabránilo volání metody.</span><span class="sxs-lookup"><span data-stu-id="02a85-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a85-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="02a85-113">See also</span></span>

- [<span data-ttu-id="02a85-114">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="02a85-114">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
