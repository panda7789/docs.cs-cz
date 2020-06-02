---
title: Entity Data Model
description: Model EDM (Entity Data Model) popisuje strukturu dat bez ohledu na jeho uložený tvar, který řeší výzvy vyplývající z ukládání dat v mnoha formulářích.
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: c98b1f4559ef297f8b11051940fd91f5f6fa06fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286737"
---
# <a name="entity-data-model"></a>Entity Data Model
Model EDM (Entity Data Model) (EDM) je sada konceptů popisujících strukturu dat bez ohledu na její uložený formulář. EDM se vypůjčuje z modelu vztahů mezi entitami, který popisuje Petr Chen ve 1976, ale také vytvoří model vztahů mezi entitami a rozšiřuje tradiční použití.  
  
 EDM řeší výzvy, které vzniknou z dat uložených v mnoha formulářích. Představte si třeba firmu, která ukládá data v relačních databázích, textových souborech, souborech XML, tabulkách a sestavách. To představuje významné problémy při modelování dat, návrhu aplikací a přístupu k datům. Při navrhování aplikace orientované na data je nutné, aby bylo možné zapisovat do efektivního a udržovatelného kódu, aniž byste se museli vzdát efektivního přístupu k datům, úložiště a škálovatelnosti. Když data mají relační strukturu, přístup k datům, úložiště a škálovatelnost jsou velmi efektivní, ale psaní efektivního a udržovatelného kódu se bude obtížnější. Když data obsahují strukturu objektu, probíhající se kompromisy: zápis efektivního a udržovatelného kódu se účtuje za cenu efektivního přístupu k datům, úložiště a škálovatelnosti. I v případě, že je možné najít správné saldo mezi těmito kompromisy, vzniknou nové výzvy při přesunu dat z jednoho formuláře do druhého. Model EDM (Entity Data Model) řeší tyto výzvy tím, že popisuje strukturu dat z pohledu entit a vztahy, které jsou nezávislé na jakémkoli schématu úložiště. Díky tomu je uložená forma dat irelevantní pro návrh a vývoj aplikací. A vzhledem k tomu, že entity a vztahy popisují strukturu dat, která se používají v aplikaci (ne v její uložené podobě), můžou se vyvíjet jako vývoj aplikace.  
  
 A `conceptual model` je konkrétní reprezentace struktury dat jako entit a vztahů a je obecně definována v jazyce specifickém pro doménu (DSL), který implementuje koncepty modelu EDM. [Konceptuální schéma definiční jazyk (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) je příkladem konkrétního jazyka specifického pro doménu. Entity a vztahy, které jsou popsány v koncepčním modelu, lze představit jako abstrakce objektů a přidružení v aplikaci. To umožňuje vývojářům soustředit se na koncepční model bez obav o schéma úložiště a umožňuje jim psát kód s efektivitou a udržovatelnosti. Díky sestupným návrhářům schémat úložiště se můžete soustředit na efektivitu přístupu k datům, úložiště a škálovatelnosti.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Témata v této části popisují koncepty model EDM (Entity Data Model). Všechny DSL, které implementují EDM, by měly obsahovat koncepty popsané tady. Všimněte si, že [ADO.NET Entity Framework](./ef/index.md) používá CSDL k definování konceptuálních modelů. Další informace najdete v tématu [specifikace CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).  
  
 [Koncepty modelu EDM (Entity Data Model)](entity-data-model-key-concepts.md)  
  
 [Model EDM (Entity Data Model): Obory názvů](entity-data-model-namespaces.md)  
  
 [Model EDM (Entity Data Model): Primitivní datové typy](entity-data-model-primitive-data-types.md)  
  
 [Model EDM (Entity Data Model): Dědičnost](entity-data-model-inheritance.md)  
  
 [association end](association-end.md)  
  
 [association end multiplicity](association-end-multiplicity.md)  
  
 [association set](association-set.md)  
  
 [association set end](association-set-end.md)  
  
 [association type](association-type.md)  
  
 [complex type](complex-type.md)  
  
 [entity container](entity-container.md)  
  
 [entity key](entity-key.md)  
  
 [entity set](entity-set.md)  
  
 [entity type](entity-type.md)  
  
 [omezující vlastnost](facet.md)  
  
 [foreign key property](foreign-key-property.md)  
  
 [model-declared function](model-declared-function.md)  
  
 [model-defined function](model-defined-function.md)  
  
 [navigation property](navigation-property.md)  
  
 [majetek](property.md)  
  
 [referential integrity constraint](referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Viz také

- [ADO.NET model EDM (Entity Data Model) nástroje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Specifikace CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
