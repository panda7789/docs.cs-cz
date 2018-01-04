---
title: "Hodnota typu č. 39; &lt;NázevTypu1&gt;& č. 39; nelze převést na & č. 39;&lt; NázevTypu2&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords: BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b583c4272dd6e964de99fb14d2795152c655f3aa
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>Hodnota typu č. 39; &lt;NázevTypu1&gt;& č. 39; nelze převést na & č. 39;&lt; NázevTypu2&gt;& č. 39;
Hodnotu typu '\<NázevTypu1 >' nelze převést na '\<NázevTypu2 > ". Neshoda typu může být kombinování odkazu na soubor s projektu odkaz na sestavení '\<assemblyname >'. Zkuste vyměnit odkaz na soubor '\<filepath >' v projektu '\<projectname1 >' s odkaz na projekt se\<projectname2 > ".  
  
 V situaci, kdy projektu vytvoří odkaz na projekt a odkaz na soubor kompilátor nezaručuje, že jeden typ lze převést na jiný.  
  
 Následující kód pseudo znázorňuje situaci, který může vytvořit tuto chybu.  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 Projekt `P1` vytváří odkaz nepřímých projektu prostřednictvím projektu `P2` do projektu `P3`a také přímý odkaz na soubor na `P3`. Prohlášení o `commonObject` používá odkaz na soubor `P3`, při volání `P2.getCommonClass` používá odkaz na projekt `P3`.  
  
 Problém v této situaci je, že odkaz na soubor Určuje název pro výstupní soubor a cesta k souboru `P3` (obvykle p3.dll), zatímco odkazů projektu identifikovat zdrojový projekt (`P3`) podle názvu projektu. Z toho důvodu nelze kompilátor zaručit, že typ `P3.commonClass` pochází z stejný zdrojový kód prostřednictvím dvou různých odkazy.  
  
 Tuto situaci obvykle dochází, když projektu odkazy a jsou kombinované odkazů na soubor. V předchozí ilustraci, nebude problém nastat, pokud `P1` provedené projektu přímý odkaz na `P3` místo odkaz na soubor.  
  
 **ID chyby:** BC30955  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Změňte odkaz na soubor odkaz na projekt.  
  
## <a name="see-also"></a>Viz také  
 [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)  
 
