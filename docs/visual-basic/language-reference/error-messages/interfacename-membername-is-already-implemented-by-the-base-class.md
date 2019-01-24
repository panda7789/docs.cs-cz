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
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>&#39;&lt;InterfaceName&gt;.&lt; MemberName&gt; &#39; je již implementováno prostřednictvím základní třídy &#39; &lt;baseclassname&gt;&#39;. Opětovná implementace &lt;typ&gt; předpokládá, že
Vlastnost, procedura nebo události v odvozené třídě používá `Implements` klauzule určující člena rozhraní, která je již implementováno základní třídy.  
  
 Odvozená třída může znovu implementovat člen rozhraní, která je implementována ve své základní třídy. Nejedná se stejně jako přepsání implementaci základní třídy. Další informace najdete v tématu [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42015  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud máte v úmyslu znovu implementovat člen rozhraní, není potřeba provádět žádnou akci. Kód v odvozené třídě přistupuje ke reimplemented člen, pokud použijete `MyBase` – klíčové slovo pro přístup k implementaci základní třídy.  
  
-   Pokud je nemáte v úmyslu znovu implementovat člen rozhraní, odeberte `Implements` klauzule v deklaraci vlastnosti, procedury nebo události.  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
