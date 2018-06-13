---
title: Procedura přetížení (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 0d1f2c4d8c88922659b3d91ed41d5e760e6e5233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653911"
---
# <a name="procedure-overloading-visual-basic"></a>Procedura přetížení (Visual Basic)
*Přetížení* procedury znamená jeho definováním v několika verze, používá stejný název, ale seznamy různých parametrů. Účelem přetížení je definovat několik úzce související verzí procedury bez nutnosti jejich odlišení podle názvu. To provedete pomocí různých seznam parametrů.  
  
## <a name="overloading-rules"></a>Přetížení pravidla  
 Pokud jste přetížení procedury, platí následující pravidla:  
  
-   **Stejný název**. Jednotlivé verze přetížené musí používat stejný název procedury.  
  
-   **Jiný podpis**. Každý přetížené verze se musí lišit od všech ostatních přetížené verzí alespoň v jedné z těchto ohledech:  
  
    -   Počet parametrů  
  
    -   Pořadí parametrů  
  
    -   Datové typy parametrů  
  
    -   Počet parametrů typu (pro obecný postup)  
  
    -   Návratový typ (pouze pro operátora převodu)  
  
     Společně s název procedury předchozí položky se souhrnně označují jako *podpis* procedury. Při volání přetížené procedury kompilátor podpis používá ke kontrole, jestli volání správně odpovídá definici.  
  
-   **Položky není součástí podpis**. Bez různých podpis nelze přetížení procedury. Nelze na konkrétní přetížení procedury pomocí různých pouze jeden nebo více z následujících položek:  
  
    -   Postup modifikátor klíčová slova, jako například `Public`, `Shared`, a `Static`  
  
    -   Typ nebo parametr názvy parametrů  
  
    -   Zadejte parametr omezení (pro obecný postup)  
  
    -   Klíčová slova – modifikátor parametrů, jako například `ByRef` a `Optional`  
  
    -   Jestli vrátí hodnotu  
  
    -   datový typ vrácené hodnoty (s výjimkou operátora převodu)  
  
     Položky v předchozím seznamu nejsou součástí podpis. I když je nemůžete použít k rozlišení mezi verzemi přetížené, můžete je lišit přetížené verze, které jsou rozlišené správně pomocí jejich podpisy.  
  
-   **Pozdní vazba argumenty**. Pokud máte v úmyslu proměnnou pozdní vázaný objekt předat přetížené verze, je potřeba deklarovat odpovídající parametr jako <xref:System.Object>.  
  
## <a name="multiple-versions-of-a-procedure"></a>Více verzí procedury  
 Předpokládejme, že jsou zápis `Sub` postup post transakce proti vyrovnávání zákazníka a chcete mít možnost k odkazování na Zákazník podle názvu nebo podle číslo účtu. K tomuto požadavku vyhovělo, můžete definovat dva různé `Sub` postupy, jako v následujícím příkladu:  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a>Přetížené verze  
 Alternativou je přetížení název jedinou proceduru. Můžete použít [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo na verzi postup pro každý seznam parametrů definujte takto:  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a>Další přetížení  
 Pokud jste chtěli také přijmout částka transakce buď `Decimal` nebo `Single`, může další přetížení `post` povolit pro tuto variantu. Pokud jste to udělali to ke každému přetížení v předchozím příkladu byste měli čtyři `Sub` postupy, všechny se stejným názvem, ale s čtyři různé podpisy.  
  
## <a name="advantages-of-overloading"></a>Výhody přetížení  
 Výhodou přetížení procedury je v flexibilitu volání. Použít `post` postup deklarované v předchozím příkladu volání kódu můžete získat Identifikace zákazníka jako buď `String` nebo `Integer`a pak zavolají stejným způsobem v obou případech. Následující příklad ilustruje toto:  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)  
 [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)  
 [Řešení přetížení](./overload-resolution.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
