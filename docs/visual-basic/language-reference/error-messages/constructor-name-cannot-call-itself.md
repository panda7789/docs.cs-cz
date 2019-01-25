---
title: Konstruktor &#39; &lt;název&gt; &#39; nemůže volat sám sebe
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 4a02277893147716098a3dcc327e221e0775d476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662722"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a><span data-ttu-id="19986-102">Konstruktor &#39; &lt;název&gt; &#39; nemůže volat sám sebe</span><span class="sxs-lookup"><span data-stu-id="19986-102">Constructor &#39;&lt;name&gt;&#39; cannot call itself</span></span>
<span data-ttu-id="19986-103">A `Sub New` postupu ve třídě nebo struktuře zavolá sama sebe.</span><span class="sxs-lookup"><span data-stu-id="19986-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="19986-104">Konstruktor slouží k inicializaci instance třídy nebo struktury při prvním vytvoření.</span><span class="sxs-lookup"><span data-stu-id="19986-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="19986-105">Třídy nebo struktury může mít několik konstruktorů, pokud mají všechny seznamy různých parametrů.</span><span class="sxs-lookup"><span data-stu-id="19986-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="19986-106">Konstruktor je povolený pro volání jiného konstruktoru k provádění svých funkcí, kromě svou vlastní.</span><span class="sxs-lookup"><span data-stu-id="19986-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="19986-107">Ale je pro konstruktor k volat sám sebe a ve skutečnosti by způsobil nekonečnou rekurzi Pokud povolena.</span><span class="sxs-lookup"><span data-stu-id="19986-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="19986-108">**ID chyby:** BC30298</span><span class="sxs-lookup"><span data-stu-id="19986-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="19986-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="19986-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="19986-110">Zkontrolujte seznam parametrů volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="19986-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="19986-111">Musí být odlišný od u konstruktoru uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="19986-111">It should be different from that of the constructor making the call.</span></span>  
  
2.  <span data-ttu-id="19986-112">Pokud je nemáte v úmyslu volání jiný konstruktor, odeberte `Sub New` zcela volání.</span><span class="sxs-lookup"><span data-stu-id="19986-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19986-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19986-113">See also</span></span>
- [<span data-ttu-id="19986-114">Doba života objektu: Způsob vytváření a zničení objektů</span><span class="sxs-lookup"><span data-stu-id="19986-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
