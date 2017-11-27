---
title: "& č. 39; &lt;interfacename&gt;.&lt; MemberName&gt;& č. 39; je už implementované základní třídy & č. 39;&lt; baseclassname&gt;& č. 39;. Opětovná implementace &lt;typ&gt; předpokládá, že"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords: BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69884ed567e0046da5cf5c51b3e83e57e890d49f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>& č. 39; &lt;interfacename&gt;.&lt; MemberName&gt;& č. 39; je už implementované základní třídy & č. 39;&lt; baseclassname&gt;& č. 39;. Opětovná implementace &lt;typ&gt; předpokládá, že
Vlastnost, postup nebo události v odvozené třídě používá `Implements` klauzule určující člena rozhraní, které je už implementované v základní třídě.  
  
 Odvozené třídy mohou přeimplementovat člena rozhraní, které je implementované její základní třída. To však není stejný jako přepsání implementaci základní třídy. Další informace najdete v tématu [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42015  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud máte v úmyslu přeimplementovat člena rozhraní, není nutné provádět žádnou akci. Kód v odvozené třídě přistupuje reimplemented člen, pokud nechcete použít `MyBase` – klíčové slovo pro přístup k implementaci základní třídy.  
  
-   Pokud jste neměli v úmyslu přeimplementovat člena rozhraní, odeberte `Implements` klauzule z deklarace vlastnosti, postup nebo událostí.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
