---
title: Podpora pro dotazy
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: e281b5ae7a41bd282f8e7c7eb9db6f99ef5487f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948940"
---
# <a name="support-for-queries"></a>Podpora pro dotazy
Úložiště instance pracovního postupu SQL zaznamenává sadu známých vlastností ve Storu. Uživatelé se mohou dotazovat na instance na základě těchto vlastností. Následující seznam obsahuje některé z těchto dobře známých vlastností:  
  
- **Název lokality** Název webu, který obsahuje službu.  
  
- **Relativní cesta k aplikaci** Cesta aplikace vzhledem k webu  
  
- **Relativní cesta služby** Cesta ke službě vzhledem k aplikaci.  
  
- **Název služby** Název služby  
  
- **Obor názvů služby** Název oboru názvů, který služba používá.  
  
- **Aktuální počítač.**  
  
- **Poslední počítač**. Počítač, ve kterém se spustila instance služby pracovního postupu naposledy.  
  
> [!NOTE]
> V případě scénářů s vlastním hostováním pomocí hostitele služby pracovního postupu se naplní jenom poslední čtyři vlastnosti. Pro scénáře aplikace pracovního postupu se naplní jenom poslední vlastnost.  
  
 Běhové prostředí pracovního postupu poskytuje hodnoty pro první tři vlastnosti. Hostitel služby pracovního postupu poskytuje hodnotu pro vlastnost **důvod pozastavení** . Vlastní úložiště instance pracovního postupu SQL poskytuje hodnoty pro **Poslední aktualizovanou vlastnost počítače** .  
  
 Funkce úložiště instance pracovního postupu SQL také umožňuje určit vlastní vlastnosti, pro které chcete ukládat hodnoty do databáze trvalosti a které chcete použít v dotazech. Další informace o vlastních propagačních akcích najdete v tématu [rozšiřitelnost úložiště](store-extensibility.md).  
  
## <a name="views"></a>Zobrazení  
 Úložiště instancí obsahuje následující zobrazení. Další podrobnosti najdete v tématu [schéma databáze trvalosti](persistence-database-schema.md) .  
  
### <a name="the-instances-view"></a>Zobrazení instance  
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
  
13. **Pozastaveno**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>Zobrazení ServiceDeployments  
 Zobrazení ServiceDeployments obsahuje následující pole:  
  
1. **Názvem**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **ServiceName**  
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>Zobrazení InstancePromotedProperties  
 Zobrazení InstancePromotedProperties obsahuje následující pole. Podrobnosti o propagovaných vlastnostech najdete v tématu [rozšiřitelnost obchodu](store-extensibility.md) .  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **PromotionName**  
  
4. **Hodnota #** (rozsah polí z **hodnota1** do **Value64**).
