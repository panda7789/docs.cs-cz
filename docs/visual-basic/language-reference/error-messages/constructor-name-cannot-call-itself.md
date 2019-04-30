---
title: Konstruktor '<name>' nemůže volat sám sebe.
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 8459ee7fec6d761161a721c88ccdc88e513fc95f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936692"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="d9996-102">Konstruktor '\<name >' nemůže volat sám sebe</span><span class="sxs-lookup"><span data-stu-id="d9996-102">Constructor '\<name>' cannot call itself</span></span>
<span data-ttu-id="d9996-103">A `Sub New` postupu ve třídě nebo struktuře zavolá sama sebe.</span><span class="sxs-lookup"><span data-stu-id="d9996-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="d9996-104">Konstruktor slouží k inicializaci instance třídy nebo struktury při prvním vytvoření.</span><span class="sxs-lookup"><span data-stu-id="d9996-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="d9996-105">Třídy nebo struktury může mít několik konstruktorů, pokud mají všechny seznamy různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="d9996-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="d9996-106">Konstruktor je povolený pro volání jiného konstruktoru k provádění svých funkcí, kromě svou vlastní.</span><span class="sxs-lookup"><span data-stu-id="d9996-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="d9996-107">Ale je pro konstruktor k volat sám sebe a ve skutečnosti by způsobil nekonečnou rekurzi Pokud povolena.</span><span class="sxs-lookup"><span data-stu-id="d9996-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="d9996-108">**ID chyby:** BC30298</span><span class="sxs-lookup"><span data-stu-id="d9996-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9996-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d9996-109">To correct this error</span></span>  
  
1. <span data-ttu-id="d9996-110">Zkontrolujte seznam parametrů volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d9996-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="d9996-111">Musí být odlišný od u konstruktoru uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="d9996-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="d9996-112">Pokud je nemáte v úmyslu volání jiný konstruktor, odeberte `Sub New` zcela volání.</span><span class="sxs-lookup"><span data-stu-id="d9996-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9996-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9996-113">See also</span></span>

- [<span data-ttu-id="d9996-114">Doba života objektu: Způsob vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="d9996-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
