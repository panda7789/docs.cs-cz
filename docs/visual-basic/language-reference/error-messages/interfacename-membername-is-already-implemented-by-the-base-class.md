---
title: '&#39;&lt;InterfaceName&gt;.&lt; MemberName&gt; &#39; je již implementováno prostřednictvím základní třídy &#39; &lt;baseclassname&gt;&#39;. Opětovná implementace &lt;typ&gt; předpokládá, že'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 22a3bd4e8c09c0d070e7fa5e75571a7215c3a274
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507197"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="22fbc-103">&#39;&lt;InterfaceName&gt;.&lt; MemberName&gt; &#39; je již implementováno prostřednictvím základní třídy &#39; &lt;baseclassname&gt;&#39;.</span><span class="sxs-lookup"><span data-stu-id="22fbc-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="22fbc-104">Opětovná implementace &lt;typ&gt; předpokládá, že</span><span class="sxs-lookup"><span data-stu-id="22fbc-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="22fbc-105">Vlastnost, procedura nebo události v odvozené třídě používá `Implements` klauzule určující člena rozhraní, která je již implementováno základní třídy.</span><span class="sxs-lookup"><span data-stu-id="22fbc-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="22fbc-106">Odvozená třída může znovu implementovat člen rozhraní, která je implementována ve své základní třídy.</span><span class="sxs-lookup"><span data-stu-id="22fbc-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="22fbc-107">Nejedná se stejně jako přepsání implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="22fbc-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="22fbc-108">Další informace najdete v tématu [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="22fbc-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="22fbc-109">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="22fbc-109">By default, this message is a warning.</span></span> <span data-ttu-id="22fbc-110">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="22fbc-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="22fbc-111">**ID chyby:** BC42015</span><span class="sxs-lookup"><span data-stu-id="22fbc-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="22fbc-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="22fbc-112">To correct this error</span></span>  
  
-   <span data-ttu-id="22fbc-113">Pokud máte v úmyslu znovu implementovat člen rozhraní, není potřeba provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="22fbc-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="22fbc-114">Kód v odvozené třídě přistupuje ke reimplemented člen, pokud použijete `MyBase` – klíčové slovo pro přístup k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="22fbc-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="22fbc-115">Pokud je nemáte v úmyslu znovu implementovat člen rozhraní, odeberte `Implements` klauzule v deklaraci vlastnosti, procedury nebo události.</span><span class="sxs-lookup"><span data-stu-id="22fbc-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22fbc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22fbc-116">See also</span></span>
- [<span data-ttu-id="22fbc-117">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="22fbc-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
