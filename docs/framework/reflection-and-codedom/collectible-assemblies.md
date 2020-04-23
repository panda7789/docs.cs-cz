---
title: Kolekční sestavení pro generování dynamických typů
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 02c7048e0321282463aa3558287d1d13c5e4f8d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180548"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Kolekční sestavení pro generování dynamických typů

*Sestavení kolekční* jsou dynamická sestavení, která lze uvolnit bez uvolnění domény aplikace, ve které byly vytvořeny. Veškerá spravovaná a nespravovaná paměť, kterou používá kolekční sestavení, a typy, které obsahuje, mohou být uvolněny. Informace, jako je název sestavení, jsou odebrány z interní tabulky.

Chcete-li povolit uvolnění, <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> použijte příznak při vytváření dynamického sestavení. Sestavení je přechodné (to znamená, nemůže být uloženo) a podléhá omezením popsaným v části [omezení pro sestavení kolekční](#restrictions-on-collectible-assemblies) . Modul CLR (Common Language Runtime) uvolní sestavení kolekční automaticky při uvolnění všech objektů přidružených k sestavení. Ve všech ostatních ohledech se kolekční sestavení vytvářejí a používají stejným způsobem jako ostatní dynamická sestavení.

## <a name="lifetime-of-collectible-assemblies"></a>Doba života kolekční sestavení

Životnost sestavení kolekční je řízena existencí odkazů na typy, které obsahuje, a objekty, které jsou vytvořeny z těchto typů. Modul CLR (Common Language Runtime) neuvolní sestavení, pokud existuje jeden nebo více z následujících typů (`T` je libovolný typ, který je definován v sestavení):

- Instance `T`.

- Instance pole `T`.

- Instance obecného typu, který má `T` jako jeden z jejích argumentů typu. To zahrnuje obecné kolekce `T`, a to i v případě, že je kolekce prázdná.

- Instance <xref:System.Type> nebo <xref:System.Reflection.Emit.TypeBuilder> , která představuje `T`.

   > [!IMPORTANT]
   > Je nutné uvolnit všechny objekty, které reprezentují části sestavení. Rozhraní <xref:System.Reflection.Emit.ModuleBuilder> , které `T` definuje odkaz na <xref:System.Reflection.Emit.TypeBuilder>, a <xref:System.Reflection.Emit.AssemblyBuilder> objekt udržuje odkaz na <xref:System.Reflection.Emit.ModuleBuilder>, takže odkazy na tyto objekty musí být uvolněny. Dokonce i existence <xref:System.Reflection.Emit.LocalBuilder> nebo, která se <xref:System.Reflection.Emit.ILGenerator> používá v rámci konstrukce `T` prevence vykládku.

- Statický odkaz na `T` jiný dynamicky definovaný typ `T1` , který je stále dosažitelný spuštěním kódu. Například `T1` může odvozovat z `T`nebo `T` může být typem parametru v metodě. `T1`

- Typ **ByRef** ke statickému poli, které patří `T`do.

- A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>nebo <xref:System.RuntimeMethodHandle> , který odkazuje na `T` součást prvku `T`.

- Instance libovolného objektu reflexe, který může být použit nepřímo nebo přímo pro přístup <xref:System.Type> k objektu, `T`který představuje. Například <xref:System.Type> objekt pro `T` lze získat z typu pole, jehož typ elementu je `T`, nebo z obecného typu, který má `T` jako argument typu.

- Metoda `M` v zásobníku volání libovolného vlákna, kde `M` je metoda `T` nebo metoda na úrovni modulu, která je definována v sestavení.

- Delegát pro statickou metodu, která je definována v modulu sestavení.

Pokud pouze jedna položka z tohoto seznamu existuje pouze pro jeden typ nebo jednu metodu v sestavení, modul runtime nemůže uvolnit sestavení.

> [!NOTE]
> Modul runtime ve skutečnosti nenačítá sestavení, dokud nejsou spuštěny finalizační metody pro všechny položky v seznamu.

Pro účely sledování životního cyklu se konstruovaný obecný typ, jako `List<int>` je například (v jazyce `List(Of Integer)` C#) nebo (v Visual Basic), který je vytvořen a použit při generování sestavení kolekční, je považován za definovaný buď v sestavení, které obsahuje definici obecného typu nebo v sestavení, které obsahuje definici jednoho z jejích argumentů typu. Přesné sestavení, které je použito, je podrobné informace o implementaci a může se změnit.

## <a name="restrictions-on-collectible-assemblies"></a>Omezení pro kolekční sestavení

Následující omezení platí pro kolekční sestavení:

- **Statické odkazy** Typy v běžném dynamickém sestavení nemohou mít statické odkazy na typy, které jsou definovány v sestavení kolekční. Například pokud definujete běžný typ, který dědí z typu v sestavení kolekční, je vyvolána <xref:System.NotSupportedException> výjimka. Typ v sestavení kolekční může mít statické odkazy na typ v jiném sestavení kolekční, ale rozšiřuje životnost odkazovaného sestavení na životnost odkazujícího sestavení.

- **Zprostředkovatel komunikace s objekty COM** V rámci kolekční sestavení nelze definovat žádná rozhraní modelu COM a žádné instance typů v rámci sestavení kolekční nelze převést na objekty modelu COM. Typ v sestavení kolekční nemůže sloužit jako obálka s možnou modelem COM (doleva) nebo obálka s možnou (RCW). Typy v sestaveních kolekční však mohou používat objekty, které implementují rozhraní COM.

- **Vyvolání platformy** Metody, které mají <xref:System.Runtime.InteropServices.DllImportAttribute> atribut, nebudou zkompilovány, pokud jsou deklarovány v sestavení kolekční. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> Instrukci nelze použít v implementaci typu v kolekční sestavení a takové typy nelze zařadit do nespravovaného kódu. Do nativního kódu však můžete zavolat pomocí vstupního bodu, který je deklarován v sestavení bez kolekční.

- **Zařazování** Objekty (zejména Delegáti), které jsou definovány v sestaveních kolekční, nelze zařadit. Toto je omezení pro všechny přechodné emitované typy.

- **Načítání sestavení** Generování reflexe je jediným mechanismem, který je podporován pro načítání sestavení kolekční. Sestavení, která jsou načtena pomocí jakékoliv jiné formy načítání sestavení, nelze uvolnit.

- **Kontextově vázané objekty** Kontext – statické proměnné nejsou podporovány. Typy v sestavení kolekční se nedají <xref:System.ContextBoundObject>zvětšit. Nicméně kód v sestaveních kolekční může používat kontextově vázané objekty, které jsou definovány jinde.

- **Vlákna – statická data** Proměnné statických vláken nejsou podporovány.

## <a name="see-also"></a>Viz také

- [Generování dynamických metod a sestavení](emitting-dynamic-methods-and-assemblies.md)
