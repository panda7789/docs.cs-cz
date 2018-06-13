---
title: 'Postupy: dotaz pro netrvalé instance'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: 000342013be4380e1a038fb8233050523f6bc758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516159"
---
# <a name="how-to-query-for-non-persisted-instances"></a>Postupy: dotaz pro netrvalé instance
Když je vytvořena nová instance služby a služby má chování ukládání Instance pracovního postupu SQL definovaný, hostitel služby vytvoří počáteční záznam pro tuto instanci služby v úložišti instance. Následně při prvním potrvají instance služby, chování ukládání Instance pracovního postupu SQL uloží aktuální stav instance společně s další data, která je požadována pro aktivaci, obnovení a řízení.  
  
 Pokud instance není trvalý po vytvoření počáteční položka pro instanci, instance služby se říká, že v netrvalého stavu. Všechny instance trvalou služby můžete dotaz a řídí. Instance služby netrvalé může být dotazována ani řídí. Pokud je instance netrvalé je pozastavená kvůli neošetřené výjimce můžete dotaz ale ovládaná nejsou.  
  
 Instance trvanlivý služby, které ještě nejsou trvalé zůstanou v netrvalého stavu v následujících scénářích:  
  
-   Hostitel služby spadne, než se instance trvalé poprvé. Původní položka pro instanci zůstává v úložišti instance. Tato instance není použitelná pro obnovení. Pokud je korelační zpráva doručena, instance zase aktivní.  
  
-   Instance dojde k neošetřené výjimce před nastavené jako trvalé, a poprvé. Následující scénáře jsou vyvolány  
  
    -   Pokud hodnota **UnhandledExceptionAction** je nastavena na **Abandon**, informace o nasazení služby je zapsán do instance úložiště a instance je uvolněn z paměti. Instance zůstane v netrvalého stavu v databázi trvalost.  
  
    -   Pokud hodnota **UnhandledExceptionAction** je nastavena na **AbandonAndSuspsend**, informace o nasazení služby je zapsána do databáze trvalosti a stav instance je nastavena na  **Pozastaveno**. Instance nelze obnovit, zrušena nebo byla ukončena. Hostitele služby nelze načíst instanci, protože instance není ještě jako trvalý, a proto není úplný záznam databáze pro instanci.  
  
    -   Pokud hodnota **UnhandledExceptionAction** je nastavena na **zrušit** nebo **ukončit**, informace o nasazení služby je zapsán do instance úložiště a stav instance je nastavený na **dokončeno**.  
  
 Ukázkové dotazy nenalezl netrvalé instance v databázi SQL trvalosti a z databáze odstranit tyto instance v následujících částech.  
  
## <a name="to-find-all-instances-not-persisted-yet"></a>Vyhledejte všechny instance není trvalý ještě  
 Následující dotaz SQL vrátí ID a vytvoření času pro všechny instance, které nejsou trvalé v databázi trvalost ještě.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;  
```  
  
## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>Najít všechny instance ještě není trvalý a také není načtená.  
 Následující dotaz SQL vrátí ID a vytvoření času pro všechny instance, které nejsou trvalé a také se nenačítají.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;  
```  
  
## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>Najít všechny pozastavené instance není trvalý ještě  
 Následující dotaz SQL vrátí ID, vytváření, Důvod pozastavení a název pozastavení výjimky pro všechny instance, které nejsou trvalé a taky v pozastaveném stavu.  
  
```  
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;  
```  
  
## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>Chcete odstranit netrvalé instancí z databáze trvalost  
 Pravidelně zkontrolujte úložiště instance k netrvalé instancí a odeberte instancí z úložiště instance, pokud jste si jistí, že instance neobdrží zprávu korelační. Například pokud instance byla v databázi několik měsíců a znáte pracovního postupu má obvykle životnost za několik dnů, je bezpečné předpokládají, že se jedná o instanci neinicializovaný, která měla došlo k chybě.  
  
 Obecně je bezpečné odstranit netrvalé instancí, které není pozastaven nebo není načtená. Nedoporučuje se mazat **všechny** netrvalé instance, protože tato instance sada obsahuje instance, které jsou právě vytvořili, ale nejsou nastavené jako trvalé ještě. Odstraňte pouze netrvalé instancí, které zbyly vzhledem k tomu, že hostitel služby pracovního postupu, který měl načíst instanci způsobila výjimku nebo instance samotného způsobila výjimku.  
  
> [!WARNING]
>  Odstraňování instancí netrvalé z obchodu instance snižuje velikost úložiště a může zvýšit výkon operací úložiště.
