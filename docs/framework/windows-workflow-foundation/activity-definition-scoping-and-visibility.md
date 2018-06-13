---
title: Nastavení oboru definici aktivity a viditelnost
ms.date: 03/30/2017
ms.assetid: ccdffa07-9503-4eea-a61b-17f1564368b7
ms.openlocfilehash: f3a8936c1bc3275468e1e4dbd23d0d001edad021
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518499"
---
# <a name="activity-definition-scoping-and-visibility"></a>Nastavení oboru definici aktivity a viditelnost
Nastavení oboru definici aktivity a viditelnost, stejně jako obor a viditelnost objektu, je schopnost jiné objekty nebo aktivity přístup ke členům aktivity. Definici aktivity provádí následující implementace:  
  
1.  Určení členů (<xref:System.Activities.Argument>, <xref:System.Activities.Variable>, a <xref:System.Activities.ActivityDelegate> objektů a podřízené aktivity) aktivitu zpřístupní svým uživatelům.  
  
2.  Implementace logiky provádění aktivity  
  
 Implementace může zahrnovat členy, které nejsou přístupné k příjemce aktivity, ale jsou místo podrobnosti implementace.  Podobně jako u definic typu, aktivity modelu umožňuje autorovi kvalifikaci viditelnost člena aktivity týkající se definice aktivity definovaný.  Tento přehled řídí aspektů člen využití, například data rozsahu.  
  
## <a name="scope"></a>Rozsah  
 Kromě dat rozsahu, viditelnost aktivity modelu můžete omezit přístup k další aspekty aktivity, jako je například ověřování, ladění, sledování nebo trasování. Provádění vlastnosti použijte viditelnost a vytváření oborů pro chovaly charakteristiky spouštění na konkrétní rozsah definice. Sekundární kořeny použít k omezení stavu zachycenou viditelnost a rozsahu <xref:System.Activities.Statements.CompensableActivity> do oboru definice, ve kterém compensable aktivity se používají.  
  
## <a name="definition-and-usage"></a>Definice a používání  
 Pracovní postup je napsaný vytvářením nové aktivity, která dědí z třídy základní aktivitě a pomocí aktivity z [předdefinované knihovna aktivit](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). Chcete-li použít aktivitu, musíte nakonfigurovat Autor aktivity viditelnost jednotlivé komponenty jeho definice.  
  
### <a name="activity-members"></a>Aktivita členy  
 Model aktivity definuje argumenty, proměnné, delegáti a podřízené aktivity, které aktivity poskytuje přístup k příjemce. Každý z těchto členů můžete být deklarována jako `public` nebo `private`. Veřejné členy nakonfigurovány uživatelem aktivity, zatímco `private` členové používat implementace pevné autorem aktivity. Viditelnost pravidla pro vytváření oboru data jsou následující:  
  
1.  Veřejné členy a veřejné členy veřejné podřízené aktivit můžete odkazovat na veřejné proměnné.  
  
2.  Členové privátní a veřejné členy veřejné podřízené aktivit můžete odkazovat argumentů a soukromé proměnné.  
  
 Člena, který můžete nastavit, že příjemci aktivity by měla být nikdy provedené privátní.  
  
### <a name="authoring-models"></a>Vytváření modelů  
 Vlastní aktivity jsou definované za použití <xref:System.Activities.NativeActivity>, <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, nebo <xref:System.Activities.AsyncCodeActivity>. Aktivity, které jsou odvozeny od tyto třídy můžete vystavit typů jiného člena s jinou visibilities.  
  
#### <a name="nativeactivity"></a>NativeActivity  
 Aktivity, které jsou odvozeny od <xref:System.Activities.NativeActivity> chovají, který je napsána v imperativní kódu a může volitelně definované za použití stávající aktivity. Odvozování aktivity z <xref:System.Activities.NativeActivity> uděluje přístup ke všem funkcím zveřejněné modulem runtime. Každý člen tuto činnost lze definovat pomocí veřejných nebo privátních viditelnost, s výjimkou argumenty, které lze deklarovat pouze jako `public`.  
  
 Členy třídy odvozené od <xref:System.Activities.NativeActivity> jsou deklarovány pomocí modulu runtime <xref:System.Activities.NativeActivityMetadata> struktura předaný <xref:System.Activities.NativeActivity.CacheMetadata%2A> metoda.  
  
#### <a name="activity"></a>Aktivita  
 Aktivity vytvořené pomocí <xref:System.Activities.Activity> chovají, který je určený výhradně prostřednictvím skládání ostatní aktivity. <xref:System.Activities.Activity> Třída má jednu podřízenou aktivitu implementace získat pomocí modulu runtime <xref:System.Activities.Activity.Implementation%2A>. Odvozování z aktivity <xref:System.Activities.Activity> můžete definovat veřejné argumenty, veřejné proměnné, importované ActivityDelegates a importované aktivity.  
  
 Importované ActivityDelegates a aktivity jsou deklarovány jako veřejné podřízené aktivity, ale nemohou být naplánovány přímo pomocí aktivity. Tyto informace se používá během ověřování, aby neběžely ověření nadřazené přístupem v umístěních, kde se nikdy neprovede aktivity. Navíc importované podřízené objekty, stejně jako veřejné podřízené objekty, můžete odkazovat a naplánované aktivity implementací. To znamená, že může obsahovat aktivitu, který importuje aktivity volá aktivity "activity1" <xref:System.Activities.Statements.Sequence> v jeho implementaci, která plánuje aktivity "activity1".  
  
#### <a name="codeactivity-asynccodeactivity"></a>CodeActivity / AsyncCodeActivity  
 Tato základní třída se používá k vytváření chování v imperativní kódu. Aktivity, které jsou odvozeny z této třídy pouze mít přístup k argumenty, které vystavují. To znamená, že pouze členové, které můžou zpřístupnit tyto aktivity jsou veřejné argumenty. Žádné členy nebo visibilities na tyto aktivity vztahovat.  
  
#### <a name="summary-of-visibilities"></a>Souhrn visibilities  
 Následující tabulka shrnuje informace dříve v této části.  
  
|Typ členu|NativeActivity|Aktivita|CodeActivity / AsyncCodeActivity|  
|-----------------|--------------------|--------------|--------------------------------------|  
|Arguments|Veřejných / privátních|Public|Není k dispozici|  
|Proměnné|Veřejných / privátních|Public|Není k dispozici|  
|Podřízené aktivity|Veřejných / privátních|Veřejné, jeden pevný privátní podřízené definované v implementaci.|Není k dispozici|  
|ActivityDelegates|Veřejných / privátních|Public|Není k dispozici|  
  
 Obecně platí člena, který nelze nastavit uživatelem aktivity by neměl být zveřejněny.  
  
### <a name="execution-properties"></a>Provádění vlastnosti  
 V některých případech je užitečné k určení rozsahu konkrétní provádění vlastnost, která má veřejné podřízené aktivity. <xref:System.Activities.ExecutionProperties> Kolekce umožňuje používat tuto funkci s <xref:System.Activities.ExecutionProperties.Add%2A> metoda. Tato metoda má logického parametru, která určuje, jestli konkrétní vlastnosti je omezená na všechny podřízené objekty, nebo jenom na ty, které jsou veřejné. Pokud tento parametr je nastaven na `true`, vlastnost budou zobrazeny pouze veřejné členy a veřejné členy jejich veřejné podřízených prvků.  
  
### <a name="secondary-roots"></a>Sekundární kořenových certifikačních autorit  
 Sekundární kořenová je interní mechanismus modulu runtime pro správu stavu aktivity honoráře. Když <xref:System.Activities.Statements.CompensableActivity> dokončil spuštěna, jeho stav není vyčistit okamžitě. Místo toho stav se spravuje pomocí modulu runtime v sekundární kořenové až po dokončení díl honoráře. Prostředí umístění zachytit pomocí kořenu sekundární odpovídají oboru definice, ve kterém se používá Compensable aktivity.
