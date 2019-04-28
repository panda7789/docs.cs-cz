---
title: Podpora pro dotazy
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641512"
---
# <a name="support-for-queries"></a>Podpora pro dotazy
Store Instance pracovního postupu SQL zaznamenává sadu dobře známé vlastnosti v úložišti. Uživatelé mohou odesílat dotazy na instance založené na těchto vlastností. Následující seznam obsahuje některé z těchto dobře známé vlastnosti:  
  
- **Název webu.** Název webu, který obsahuje službu.  
  
- **Cesta relativní aplikace.** Cesta k aplikaci vzhledem k webu.  
  
- **Cesta relativní služby.** Cesta ke službě vzhledem k aplikaci.  
  
- **Název služby.** Název služby  
  
- **Služba Namespace.** Název oboru názvů, který služba používá.  
  
- **Aktuálním počítači.**  
  
- **Poslední počítač**. Počítač, na kterém běžel instance služby pracovního postupu posledního.  
  
> [!NOTE]
>  Pro scénáře, v místním prostředí pomocí hostitele služby pracovního postupu naplní se pouze poslední čtyři vlastnosti. U scénářů s aplikace pracovního postupu se vyplní pouze poslední vlastnost.  
  
 Hodnoty pro první tři vlastnosti dodá modul runtime pracovního postupu. Poskytuje hodnoty pro tohoto hostitele služby pracovního postupu **pozastavit důvod** vlastnost. Určuje hodnoty pro Store Instance pracovního postupu SQL, samotný **poslední aktualizovat počítač** vlastnost.  
  
 Funkce SQL Store Instance pracovního postupu také umožňuje určit, že vlastní vlastnosti, pro které chcete hodnoty uložte do databáze trvalosti a, které chcete použít v dotazech. Další informace o vlastních propagačních akcí, naleznete v tématu [Store rozšíření](store-extensibility.md).  
  
## <a name="views"></a>Zobrazení  
 V úložišti instancí obsahuje následující zobrazení. Zobrazit [schéma databáze trvalosti](persistence-database-schema.md) další podrobnosti.  
  
### <a name="the-instances-view"></a>Zobrazení instancí  
 Zobrazení instance obsahuje následující pole:  
  
1. **ID**  
  
2. **PendingTimer**  
  
3. **CreationTime**  
  
4. **LastUpdatedTime**  
  
5. **ServiceDeploymentId**  
  
6. **SuspensionExceptionName**  
  
7. **SuspensionReason**  
  
8. **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>Zobrazení ServiceDeployments  
 Zobrazení ServiceDeployments obsahuje následující pole:  
  
1. **Název webu**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **ServiceName**  
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>Zobrazení InstancePromotedProperties  
 Zobrazení InstancePromotedProperties obsahuje následující pole. Podrobnosti o propagované vlastnosti, najdete v článku [Store rozšíření](store-extensibility.md) tématu.  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **PromotionName**  
  
4. **Hodnota #** (rozsah pole z **hodnota1** k **Value64**).
