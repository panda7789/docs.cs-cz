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
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>'\<interfacename>.\<membername>' je už implementované základní třídou '\<baseclassname>'. Předpokládá se opětovná implementace \<type>.
Vlastnost, procedura nebo událost v odvozené třídě používá `Implements` klauzuli určující člena rozhraní, který je již implementován v základní třídě.  
  
 Odvozená třída může znovu implementovat člen rozhraní, který je implementován svou základní třídou. To není stejné jako přepsání implementace základní třídy. Další informace naleznete v tématu [Implements](../statements/implements-clause.md).  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42015  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud máte v úmyslu znovu implementovat člena rozhraní, nemusíte provádět žádnou akci. Kód v odvozené třídě přistupuje k znovu implementovanému členu, pokud nepoužijete `MyBase` klíčové slovo pro přístup k implementaci základní třídy.  
  
- Pokud nechcete znovu implementovat člena rozhraní, odeberte `Implements` klauzuli z deklarace vlastnosti, procedury nebo události.  
  
## <a name="see-also"></a>Viz také

- [Rozhraní](../../programming-guide/language-features/interfaces/index.md)
