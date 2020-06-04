---
title: "'<interfacename>.<membername>' je už implementované základní třídou '<baseclassname>'. Předpokládá se opětovná implementace <type>."
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 6525ae08b90cc530a8f6a469d35d9ab8c27fb5e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402821"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="8e6df-103">'\<interfacename>.\<membername>' je už implementované základní třídou '\<baseclassname>'.</span><span class="sxs-lookup"><span data-stu-id="8e6df-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="8e6df-104">Předpokládá se opětovná implementace \<type>.</span><span class="sxs-lookup"><span data-stu-id="8e6df-104">Re-implementation of \<type> assumed</span></span>
<span data-ttu-id="8e6df-105">Vlastnost, procedura nebo událost v odvozené třídě používá `Implements` klauzuli určující člena rozhraní, který je již implementován v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="8e6df-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="8e6df-106">Odvozená třída může znovu implementovat člen rozhraní, který je implementován svou základní třídou.</span><span class="sxs-lookup"><span data-stu-id="8e6df-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="8e6df-107">To není stejné jako přepsání implementace základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8e6df-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="8e6df-108">Další informace naleznete v tématu [Implements](../statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8e6df-108">For more information, see [Implements](../statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="8e6df-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="8e6df-109">By default, this message is a warning.</span></span> <span data-ttu-id="8e6df-110">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8e6df-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8e6df-111">**ID chyby:** BC42015</span><span class="sxs-lookup"><span data-stu-id="8e6df-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8e6df-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8e6df-112">To correct this error</span></span>  
  
- <span data-ttu-id="8e6df-113">Pokud máte v úmyslu znovu implementovat člena rozhraní, nemusíte provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="8e6df-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="8e6df-114">Kód v odvozené třídě přistupuje k znovu implementovanému členu, pokud nepoužijete `MyBase` klíčové slovo pro přístup k implementaci základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8e6df-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
- <span data-ttu-id="8e6df-115">Pokud nechcete znovu implementovat člena rozhraní, odeberte `Implements` klauzuli z deklarace vlastnosti, procedury nebo události.</span><span class="sxs-lookup"><span data-stu-id="8e6df-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e6df-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e6df-116">See also</span></span>

- [<span data-ttu-id="8e6df-117">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e6df-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
