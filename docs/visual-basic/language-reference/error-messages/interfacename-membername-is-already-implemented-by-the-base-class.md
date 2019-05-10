---
title: "'<interfacename>. <membername>'je již implementováno prostřednictvím základní třídy'<baseclassname>'. Opětovná implementace <type> předpokládá, že"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 5943eff5fa7e68da9905e3e589eea264c06943c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593320"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>'\<interfacename >. \<membername >' je již implementováno prostřednictvím základní třídy\<baseclassname >'. Opětovná implementace \<typ > předpokládá, že
Vlastnost, procedura nebo události v odvozené třídě používá `Implements` klauzule určující člena rozhraní, která je již implementováno základní třídy.  
  
 Odvozená třída může znovu implementovat člen rozhraní, která je implementována ve své základní třídy. Nejedná se stejně jako přepsání implementaci základní třídy. Další informace najdete v tématu [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42015  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud máte v úmyslu znovu implementovat člen rozhraní, není potřeba provádět žádnou akci. Kód v odvozené třídě přistupuje ke reimplemented člen, pokud použijete `MyBase` – klíčové slovo pro přístup k implementaci základní třídy.  
  
- Pokud je nemáte v úmyslu znovu implementovat člen rozhraní, odeberte `Implements` klauzule v deklaraci vlastnosti, procedury nebo události.  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
