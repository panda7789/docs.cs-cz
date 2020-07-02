---
ms.openlocfilehash: 3eab96149be1e40d528cfd552bbe05ca766cf4e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619993"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System. Threading. Tasks. Task již nevyvolává ObjectDisposedException po uvolnění objektu.

#### <a name="details"></a>Podrobnosti

S výjimkou <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle> , <xref:System.Threading.Tasks.Task?displayProperty=fullName> metody již nevyvolávají <xref:System.ObjectDisposedException?displayProperty=fullName> výjimku po vyřazení objektu. Tato změna podporuje používání úkolů v mezipaměti. Například metoda může vrátit úlohu uloženou v mezipaměti pro zastupování již dokončené operace namísto přidělení nové úlohy. To nebylo v předchozích verzích rozhraní .NET Framework možné, protože příjemci úlohy s ní mohli nakládat.

#### <a name="suggestion"></a>Návrh

Uvědomte si, že metody úloh již nemusí být <xref:System.ObjectDisposedException?displayProperty=fullName> v případě uvolnění objektu vyhozeny. Pokud byla aplikace v závislosti na této výjimce známa s tím, že byla úloha vyřazena, měla by být aktualizována tak, aby explicitně kontrolovala stav úlohy pomocí <xref:System.Threading.Tasks.Task.Status> .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime|
