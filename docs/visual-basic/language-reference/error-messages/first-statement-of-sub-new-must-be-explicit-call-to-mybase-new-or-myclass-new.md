---
title: "Prvním příkazem této procedury 'Sub New' musí být explicitní volání 'MyBase.New' nebo 'MyClass.New', protože konstruktor '<constructorname>' v třídě Base '<baseclassname>' pro '<derivedclassname>' je označen jako zastaralý: <errormessage>"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 33dd15e3f5f5538963597f2b00f4214895e1f47a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403002"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a><span data-ttu-id="f6da0-102">Prvním příkazem této procedury 'Sub New' musí být explicitní volání 'MyBase.New' nebo 'MyClass.New', protože konstruktor '\<constructorname>' v třídě Base '\<baseclassname>' pro '\<derivedclassname>' je označen jako zastaralý: \<errormessage></span><span class="sxs-lookup"><span data-stu-id="f6da0-102">First statement of this 'Sub New' must be an explicit call to 'MyBase.New' or 'MyClass.New' because the '\<constructorname>' in the base class '\<baseclassname>' of '\<derivedclassname>' is marked obsolete: '\<errormessage>'</span></span>
<span data-ttu-id="f6da0-103">Konstruktor třídy explicitně nevolá konstruktor základní třídy a implicitní konstruktor základní třídy je označen <xref:System.ObsoleteAttribute> atributem a direktivou, která má být považována za chybu.</span><span class="sxs-lookup"><span data-stu-id="f6da0-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="f6da0-104">Když konstruktor odvozené třídy nevolá konstruktor základní třídy, Visual Basic se pokusí vygenerovat implicitní volání konstruktoru základní třídy bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="f6da0-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="f6da0-105">Pokud není k dispozici žádný konstruktor v základní třídě, který lze volat bez argumentů, Visual Basic nemůže generovat implicitní volání.</span><span class="sxs-lookup"><span data-stu-id="f6da0-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="f6da0-106">V tomto případě je požadovaný konstruktor označen <xref:System.ObsoleteAttribute> atributem, takže Visual Basic nemůže volat.</span><span class="sxs-lookup"><span data-stu-id="f6da0-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="f6da0-107">Můžete označit libovolný prvek programování, který se už nepoužívá, a to tak, že <xref:System.ObsoleteAttribute> se na něj aplikuje.</span><span class="sxs-lookup"><span data-stu-id="f6da0-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="f6da0-108">Pokud to uděláte, můžete vlastnost atributu nastavit <xref:System.ObsoleteAttribute.IsError%2A> na buď `True` nebo `False` .</span><span class="sxs-lookup"><span data-stu-id="f6da0-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="f6da0-109">Nastavíte-li na `True` , kompilátor považuje pokus o použití prvku jako chyby.</span><span class="sxs-lookup"><span data-stu-id="f6da0-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="f6da0-110">Nastavíte-li na `False` nebo jako výchozí `False` , kompilátor vydá upozornění, pokud dojde k pokusu o použití prvku.</span><span class="sxs-lookup"><span data-stu-id="f6da0-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="f6da0-111">**ID chyby:** BC30920</span><span class="sxs-lookup"><span data-stu-id="f6da0-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6da0-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f6da0-112">To correct this error</span></span>  
  
1. <span data-ttu-id="f6da0-113">Projděte si chybovou zprávu v uvozovkách a proveďte příslušnou akci.</span><span class="sxs-lookup"><span data-stu-id="f6da0-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2. <span data-ttu-id="f6da0-114">Zahrňte volání `MyBase.New()` nebo `MyClass.New()` jako první příkaz `Sub New` v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="f6da0-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6da0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6da0-115">See also</span></span>

- [<span data-ttu-id="f6da0-116">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="f6da0-116">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
