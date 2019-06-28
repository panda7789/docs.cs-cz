---
title: 'Postupy: Dotaz na netrvalé instance'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: 87b29ce6a5858872929cea4408d0d7bcc1b378d1
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425321"
---
# <a name="how-to-query-for-non-persisted-instances"></a>Postupy: Dotaz na netrvalé instance

Když je vytvořena nová instance služby a služby má Store Instance pracovního postupu SQL chování definované, hostitel služby vytvoří počáteční záznam pro tuto instanci služby v úložišti instancí. Následně, když bude instance služby opakuje poprvé, chování Store Instance pracovního postupu SQL ukládá aktuální stav instance společně s další data, která je vyžadováno pro aktivaci, obnovení a ovládací prvek.

Pokud instance není zachována po vytvoření počáteční položkou pro instanci, se říká, že instance služby dočasný stav. Všechny instance trvalé služby můžete dotazovat a řídit. Služba netrvalé instance nejde dotazovat ani řídit. Pokud je netrvalé instance je pozastavena z důvodu neošetřené výjimky může být dotazována ale ovládaná nejsou.

Instance služby, které nejsou ještě zachované zůstanou ve stavu netrvalé v následujících scénářích:

- Hostitel služby spadne, než se instance trvale uložena poprvé. Počáteční položka pro instanci zůstává v úložišti instancí. Instance se nedá vrátit zpátky. Pokud je korelační přijetí e-mailu, bude instance aktivní znovu.

- Instance dojde k neošetřené výjimce předtím, než jej jako trvalý poprvé. Vznikají následující scénáře

  - Pokud hodnota **UnhandledExceptionAction** je nastavena na **opustit**, informace o nasazení služby se zapisují do úložiště instancí a instance je uvolněna z paměti. Instance zůstane v netrvalého stavu databáze trvalosti.

  - Pokud hodnota **UnhandledExceptionAction** je nastavena na **AbandonAndSuspend**, informace o nasazení služby je zapsána do databáze trvalosti a stav instance je nastavená na  **Pozastavit**. Instance se nedá obnovit, zrušena nebo byl ukončen. Hostitele služby nelze načíst instanci, protože instance nebyla dosud trvale uložena, a proto není úplná položka pro instanci databáze.

  - Pokud hodnota **UnhandledExceptionAction** je nastavena na **zrušit** nebo **Terminate**, informace o nasazení služby jsou zapsána do úložiště instancí a stav instance je nastavený na **dokončeno**.

Ukázkové dotazy a najít netrvalé instance databáze trvalosti SQL z databáze odstranit tyto instance v následujících částech.

## <a name="to-find-all-instances-not-persisted-yet"></a>Najít všechny instance není zachována ještě

Následující dotaz SQL vrátí ID a vytváření čas potřebný pro všechny instance, které nejsou v trvalé databáze trvalosti ještě.

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;
```

## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>Najít všechny instance ještě není trvalý a také není načtená.
 Následující dotaz SQL vrací ID a vytváření čas v rámci všech instancí, které nejsou trvale uložila a také se nenačítají.

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;
```

## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>Najít všechny pozastavené instance není zachována ještě

Následující dotaz SQL vrátí ID, čas vytvoření, pozastavení a pozastavení název výjimky pro všechny instance, které nejsou trvalé a také v pozastaveném stavu.

```sql
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;
```

## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>Chcete-li odstranit z databáze trvalosti netrvalé instance

Pravidelně zkontrolujte úložiště instance k netrvalé instance a odebrání instance v úložišti instancí, pokud jste si jistí, že instance neobdrží zprávu korelační. Například pokud víte, že pracovní postup má obvykle životnost pár dní instance je už v databázi několik měsíců, by se dá předpokládat, že se jedná o neinicializované instanci, která měla došlo k chybě.

Obecně je můžete bezpečně odstranit netrvalé instance, které není pozastavená nebo není načtený. Nedoporučuje se mazat **všechny** netrvalé instance, protože tato instance sada obsahuje instance, které jsou právě vytvořili, ale nejsou trvalé ještě. Odstranit, pouze netrvalé instance, které zbyly protože hostitele služby pracovního postupu, který se má načíst instanci způsobila výjimku nebo instanci samotné způsobila výjimku.

> [!WARNING]
> Odstranění z úložiště instance netrvalé instance snižuje velikost úložiště a může zlepšit výkon operace úložiště.
