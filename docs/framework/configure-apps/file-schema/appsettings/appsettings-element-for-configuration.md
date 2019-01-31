---
title: <appSettings> – element pro element <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dcdf8d0f11ae65353da08bba1f8d2fe5ab415c6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289585"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="1768c-102">\<appSettings > – element pro \<configuration ></span><span class="sxs-lookup"><span data-stu-id="1768c-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="1768c-103">Obsahuje vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="1768c-103">Contains custom application settings.</span></span> <span data-ttu-id="1768c-104">Toto je předdefinovaný konfigurační oddíl poskytuje rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1768c-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="1768c-105">[**\<Konfigurace >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1768c-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="1768c-106">&nbsp;&nbsp;**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="1768c-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1768c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1768c-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="1768c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="1768c-108">Attribute</span></span>

|           | <span data-ttu-id="1768c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="1768c-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="1768c-110">**Soubor**</span><span class="sxs-lookup"><span data-stu-id="1768c-110">**file**</span></span>  | <span data-ttu-id="1768c-111">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1768c-111">Optional attribute.</span></span><br><br><span data-ttu-id="1768c-112">Určuje relativní cestu na externí soubor, který obsahuje vlastní nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="1768c-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="1768c-113">Zadaný soubor obsahuje stejný druh nastavení, které jsou určené v  **\<Přidat >**,  **\<odebrat >**, a  **\<vymazat >** prvků a používá tyto prvky formátování stejného páru klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="1768c-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="1768c-114">Zadaná cesta je relativní vzhledem k hlavní konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="1768c-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="1768c-115">Pro aplikace Windows Forms, je to binární složka (například */bin/debug*), ne však umístění konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1768c-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="1768c-116">Pro aplikace webových formulářů, cesta je relativní vzhledem k kořenový adresář aplikace, kde *web.config* se nachází soubor.</span><span class="sxs-lookup"><span data-stu-id="1768c-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="1768c-117">Všimněte si, že modul runtime ignorovat atribut, pokud zadaný soubor nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="1768c-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="1768c-118">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="1768c-118">Parent element</span></span>

|     | <span data-ttu-id="1768c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1768c-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1768c-120">**\<Konfigurace >** – Element</span><span class="sxs-lookup"><span data-stu-id="1768c-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="1768c-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1768c-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="1768c-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="1768c-122">Child elements</span></span>

|     | <span data-ttu-id="1768c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="1768c-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1768c-124">**\<add>**</span><span class="sxs-lookup"><span data-stu-id="1768c-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="1768c-125">Přidá nastavení vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="1768c-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="1768c-126">**\<Vymazat >**</span><span class="sxs-lookup"><span data-stu-id="1768c-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="1768c-127">Vymaže všechny dříve definované aplikaci nastavení.</span><span class="sxs-lookup"><span data-stu-id="1768c-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="1768c-128">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="1768c-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="1768c-129">Odebere nastavení dříve definované aplikace.</span><span class="sxs-lookup"><span data-stu-id="1768c-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1768c-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1768c-130">Remarks</span></span>

<span data-ttu-id="1768c-131"> *\*\<AppSettings >** element ukládá informace o konfiguraci vlastních aplikací, jako jsou databázové připojovací řetězce, cesty k souborům, adresy URL XML webových služeb nebo nějakých jiných informací vlastní konfigurace pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="1768c-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="1768c-132">Páry klíč/hodnota zadaná v  **\<appSettings >** element jsou přístupné z kódu pomocí <xref:System.Configuration.ConfigurationSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="1768c-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="1768c-133">Můžete použít **souboru** atribut  **\<appSettings >** elementu *Web.config* a konfiguračních souborů aplikace.</span><span class="sxs-lookup"><span data-stu-id="1768c-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="1768c-134">Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepíše nastavení zadaná  **\<appSettings >** elementu.</span><span class="sxs-lookup"><span data-stu-id="1768c-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="1768c-135">**Souboru** atribut lze použít v týmu vývoje scénářích správy zdrojového kódu, jako je například, pokud uživatel požaduje přepsat nastavení projektu zadané v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1768c-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="1768c-136">Konfigurační soubory, které jsou určené **souboru** atribut musí mít kořenový uzel  **\<appSettings >** spíše než  **\<konfigurace >**.</span><span class="sxs-lookup"><span data-stu-id="1768c-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="1768c-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="1768c-137">Example</span></span>

<span data-ttu-id="1768c-138">Následující příklad ukazuje soubor nastavení externí aplikace (*custom.config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="1768c-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="1768c-139">Následující příklad ukazuje konfigurační soubor aplikace, která načítá nastavení v souboru externích nastavení a nastaví vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="1768c-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="1768c-140">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="1768c-140">Configuration file</span></span>

<span data-ttu-id="1768c-141">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine.config*), a *Web.config* soubory, které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="1768c-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="1768c-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1768c-142">See also</span></span>

- [<span data-ttu-id="1768c-143">Schéma konfiguračního souboru pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1768c-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
