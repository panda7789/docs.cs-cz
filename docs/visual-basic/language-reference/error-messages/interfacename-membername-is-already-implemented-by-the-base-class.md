---
title: '&#39;&lt;InterfaceName&gt;.&lt; MemberName&gt; &#39; je už implementované v základní třídě &#39; &lt;baseclassname&gt;&#39;. Opětovná implementace &lt;typ&gt; předpokládá, že'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 9054c293ede9db4637f23579407f2f76db29f2ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588967"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="9eda0-103">&#39;&lt;InterfaceName&gt;.&lt; MemberName&gt; &#39; je už implementované v základní třídě &#39; &lt;baseclassname&gt;&#39;.</span><span class="sxs-lookup"><span data-stu-id="9eda0-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="9eda0-104">Opětovná implementace &lt;typ&gt; předpokládá, že</span><span class="sxs-lookup"><span data-stu-id="9eda0-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="9eda0-105">Vlastnost, postup nebo události v odvozené třídě používá `Implements` klauzule určující člena rozhraní, které je už implementované v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="9eda0-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="9eda0-106">Odvozené třídy mohou přeimplementovat člena rozhraní, které je implementované její základní třída.</span><span class="sxs-lookup"><span data-stu-id="9eda0-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="9eda0-107">To však není stejný jako přepsání implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="9eda0-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="9eda0-108">Další informace najdete v tématu [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9eda0-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="9eda0-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="9eda0-109">By default, this message is a warning.</span></span> <span data-ttu-id="9eda0-110">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9eda0-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="9eda0-111">**ID chyby:** BC42015</span><span class="sxs-lookup"><span data-stu-id="9eda0-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9eda0-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9eda0-112">To correct this error</span></span>  
  
-   <span data-ttu-id="9eda0-113">Pokud máte v úmyslu přeimplementovat člena rozhraní, není nutné provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="9eda0-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="9eda0-114">Kód v odvozené třídě přistupuje reimplemented člen, pokud nechcete použít `MyBase` – klíčové slovo pro přístup k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="9eda0-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="9eda0-115">Pokud jste neměli v úmyslu přeimplementovat člena rozhraní, odeberte `Implements` klauzule z deklarace vlastnosti, postup nebo událostí.</span><span class="sxs-lookup"><span data-stu-id="9eda0-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eda0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9eda0-116">See Also</span></span>  
 [<span data-ttu-id="9eda0-117">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="9eda0-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
