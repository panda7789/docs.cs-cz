---
title: Určení oboru definici aktivity a viditelnosti
ms.date: 03/30/2017
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
ms.openlocfilehash: 7b09ac6d27dd3be502c98ce3ac0a90f636714fc2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723839"
---
# <a name="activity-definition-scoping-and-visibility"></a>Určení oboru definici aktivity a viditelnosti
Určení oboru definici aktivity a viditelnost, stejně jako obor a viditelnost objektu, je schopnost jiné objekty nebo aktivity pro přístup ke členům aktivity. Definice aktivity provádí následující implementace:  
  
1.  Určení členů (<xref:System.Activities.Argument>, <xref:System.Activities.Variable>, a <xref:System.Activities.ActivityDelegate> objektů a podřízené aktivity) aktivita poskytuje svým uživatelům.  
  
2.  Implementace logiky provádění aktivity  
  
 Implementace může zahrnovat členy, které nejsou přístupné spotřebitelům aktivity, ale spíše podrobnosti implementace.  Podobně jako u definice typu, model aktivity umožňuje autorovi k určení, zda se na člena aktivity týkající se definice aktivity definuje.  Tento přehled řídí aspekty člen využití, jako je například rozsah data.  
  
## <a name="scope"></a>Rozsah  
 Kromě zkoumání dat, aktivity viditelnost modelu můžete omezit přístup k další aspekty aktivity, jako je například ověřování, ladění, sledování a trasování. Vlastnosti spuštění pomocí viditelnost a nastavování jejich oborů pro omezení vlastností spuštění na konkrétní rozsah definice. Sekundární kořeny použít k omezení stavu nezachytává viditelnost a nastavování jejich oborů <xref:System.Activities.Statements.CompensableActivity> do oboru definice, ve kterém jsou použity kompenzovatelné aktivity.  
  
## <a name="definition-and-usage"></a>Definice a používání  
 Pracovní postup je vytvořená systémem vytváření nové aktivity dědění ze třídy základní aktivity a pomocí aktivity [knihovna předdefinovaných aktivit](net-framework-4-5-built-in-activity-library.md). Chcete-li použít aktivitu, autorem aktivity musí nakonfigurovat viditelnost všech komponent v její definici.  
  
### <a name="activity-members"></a>Aktivita členy  
 Model aktivity definuje argumenty, proměnné, delegáty a podřízené aktivity, které uživatelům zpřístupní aktivity. Každý z těchto členů lze deklarovat jako `public` nebo `private`. Veřejné členy jsou nakonfigurované uživatelem je aktivita, zatímco `private` členy použita implementace oprava autorem aktivity. Pravidla viditelnosti pro zkoumání dat jsou následující:  
  
1.  Veřejné členy a veřejné členy veřejné podřízené aktivity může odkazovat na veřejné proměnné.  
  
2.  Soukromé členy a veřejné členy veřejné podřízené aktivity může odkazovat na privátních proměnných a argumentů.  
  
 Člen, který lze nastavit spotřebitelem aktivity by měla být nikdy proveden privátní.  
  
### <a name="authoring-models"></a>Vytváření modelů  
 Vlastní aktivity jsou definované pomocí <xref:System.Activities.NativeActivity>, <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, nebo <xref:System.Activities.AsyncCodeActivity>. Aktivity, které jsou odvozeny z těchto tříd mohou vystavit typy jiný člen s různá viditelnost.  
  
#### <a name="nativeactivity"></a>Objekt NativeActivity  
 Aktivity, které jsou odvozeny z <xref:System.Activities.NativeActivity> mají chování, která je napsána v imperativního kódu a může volitelně definované pomocí existujících aktivit. Odvozování z aktivity <xref:System.Activities.NativeActivity> uděluje přístup ke všem funkcím vystavené modulu runtime. Každý člen tyto aktivity lze definovat pomocí veřejných nebo privátních viditelnost, s výjimkou argumenty, které se dají deklarovat jenom jako `public`.  
  
 Členy třídy odvozené z <xref:System.Activities.NativeActivity> jsou deklarovány pomocí modulu runtime <xref:System.Activities.NativeActivityMetadata> předat strukturu <xref:System.Activities.NativeActivity.CacheMetadata%2A> metody.  
  
#### <a name="activity"></a>Aktivita  
 Aktivity vytvořené pomocí <xref:System.Activities.Activity> mají chování, která je navržená výhradně prostřednictvím vytváření dalších aktivit. <xref:System.Activities.Activity> Třída má jednu podřízenou aktivitu implementace získat pomocí modulu runtime <xref:System.Activities.Activity.Implementation%2A>. Aktivita odvozený od <xref:System.Activities.Activity> můžete definovat argumenty veřejné, veřejné proměnné, importované delegátů aktivit ActivityDelegates a importované aktivity.  
  
 Importované delegátů aktivit ActivityDelegates a aktivit jsou deklarovány jako veřejné podřízené aktivity, ale nelze přímo plánovat aktivitou. Tyto informace se používá při ověřování vyhnout se spouštění nadřazené přístupem k ověření na místech, kde se nikdy neprovede aktivity. Navíc importované podřízené položky, stejně jako veřejné podřízené položky, můžete odkazovat a naplánovat implementaci aktivity. To znamená, že může obsahovat aktivity, který importuje aktivity volá aktivity "activity1" <xref:System.Activities.Statements.Sequence> v jeho provádění, která plánuje aktivity "activity1".  
  
#### <a name="codeactivity-asynccodeactivity"></a>CodeActivity nebo AsyncCodeActivity  
 Tato základní třída se používá k vytváření chování v imperativního kódu. Aktivity, které jsou odvozeny z této třídy mít přístup jenom k argumenty, které vystavují. To znamená, že pouze členy, kteří tyto aktivity mohou vystavit veřejný argumenty. Žádné jiné členy nebo viditelnosti vztahovat na tyto aktivity.  
  
#### <a name="summary-of-visibilities"></a>Souhrnné informace o viditelnosti  
 Následující tabulka shrnuje informace uvedené v této části.  
  
|Typ členu|Objekt NativeActivity|Aktivita|CodeActivity nebo AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|Arguments|Veřejného a soukromého|Public|Není k dispozici|  
|Proměnné|Veřejného a soukromého|Public|Není k dispozici|  
|Podřízené aktivity|Veřejného a soukromého|Veřejné, jeden dlouhodobý soukromé podřízené definované v implementaci.|Není k dispozici|  
|ActivityDelegates|Veřejného a soukromého|Public|Není k dispozici|  
  
 Obecně platí člena, který nelze nastavit spotřebitelem aktivity by neměl být zveřejněny.  
  
### <a name="execution-properties"></a>Vlastnosti spuštění  
 V některých případech je užitečná k určení rozsahu vlastnost konkrétní spuštění pro veřejné podřízené aktivity. <xref:System.Activities.ExecutionProperties> Kolekce poskytuje tato funkce se <xref:System.Activities.ExecutionProperties.Add%2A> metody. Tato metoda má parametr logické hodnoty označující, zda určité vlastnosti působí na všechny podřízené objekty, nebo jenom na ty, které jsou veřejné. Pokud tento parametr je nastaven na `true`, vlastnost budou zobrazeny pouze veřejné členy a veřejné členy svých veřejných podřízených položek.  
  
### <a name="secondary-roots"></a>Sekundární kořeny  
 Sekundární kořenový adresář je modul runtime interní nástroj pro správu stavu aktivity kompenzace. Když <xref:System.Activities.Statements.CompensableActivity> dokončení spuštěné, jeho stav není vyčištění okamžitě. Místo toho se stav udržuje modulem runtime sekundární kořenového až do dokončení epizodě kompenzace. Umístění prostředí zachytit pomocí sekundární kořenové odpovídají oboru definice, ve kterém se používá Kompenzovatelné aktivity.
