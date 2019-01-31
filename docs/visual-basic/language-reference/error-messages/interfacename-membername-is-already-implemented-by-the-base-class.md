---
title: "'<interfacename>. <membername>'je již implementováno prostřednictvím základní třídy'<baseclassname>\". Opětovná implementace <type> předpokládá, že"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 5d5d9f21069c7b9aa54940525b7678bc3987b77c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264148"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="85ad8-103">"\<interfacename >. \<membername >' je již implementováno prostřednictvím základní třídy\<baseclassname >'.</span><span class="sxs-lookup"><span data-stu-id="85ad8-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="85ad8-104">Opětovná implementace \<typ > předpokládá, že</span><span class="sxs-lookup"><span data-stu-id="85ad8-104">Re-implementation of \<type> assumed</span></span>
<span data-ttu-id="85ad8-105">Vlastnost, procedura nebo události v odvozené třídě používá `Implements` klauzule určující člena rozhraní, která je již implementováno základní třídy.</span><span class="sxs-lookup"><span data-stu-id="85ad8-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="85ad8-106">Odvozená třída může znovu implementovat člen rozhraní, která je implementována ve své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="85ad8-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="85ad8-107">Nejedná se stejně jako přepsání implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="85ad8-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="85ad8-108">Další informace najdete v tématu [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="85ad8-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="85ad8-109">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="85ad8-109">By default, this message is a warning.</span></span> <span data-ttu-id="85ad8-110">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="85ad8-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="85ad8-111">**ID chyby:** BC42015</span><span class="sxs-lookup"><span data-stu-id="85ad8-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="85ad8-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="85ad8-112">To correct this error</span></span>  
  
-   <span data-ttu-id="85ad8-113">Pokud máte v úmyslu znovu implementovat člen rozhraní, není potřeba provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="85ad8-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="85ad8-114">Kód v odvozené třídě přistupuje ke reimplemented člen, pokud použijete `MyBase` – klíčové slovo pro přístup k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="85ad8-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="85ad8-115">Pokud je nemáte v úmyslu znovu implementovat člen rozhraní, odeberte `Implements` klauzule v deklaraci vlastnosti, procedury nebo události.</span><span class="sxs-lookup"><span data-stu-id="85ad8-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ad8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85ad8-116">See also</span></span>
- [<span data-ttu-id="85ad8-117">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="85ad8-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
