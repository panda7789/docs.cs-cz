---
title: "Kolekcemi schémat OLE DB"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9b88308c5dad69ed1ba6f48f525931e94f13ef1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="f0744-102">Kolekcemi schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="f0744-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="f0744-103">Tato část popisuje podporu kolekci schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="f0744-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="f0744-104">Zprostředkovatel Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="f0744-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="f0744-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="f0744-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f0744-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="f0744-106">Tables</span></span>  
  
-   <span data-ttu-id="f0744-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="f0744-107">Columns</span></span>  
  
-   <span data-ttu-id="f0744-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="f0744-108">Procedures</span></span>  
  
-   <span data-ttu-id="f0744-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f0744-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f0744-110">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f0744-110">Catalog</span></span>  
  
-   <span data-ttu-id="f0744-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="f0744-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="f0744-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="f0744-112">Tables</span></span>  
  
|<span data-ttu-id="f0744-113">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-113">ColumnName</span></span>|<span data-ttu-id="f0744-114">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-115">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-116">String</span><span class="sxs-lookup"><span data-stu-id="f0744-116">String</span></span>|  
|<span data-ttu-id="f0744-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-118">String</span><span class="sxs-lookup"><span data-stu-id="f0744-118">String</span></span>|  
|<span data-ttu-id="f0744-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-119">TABLE_NAME</span></span>|<span data-ttu-id="f0744-120">String</span><span class="sxs-lookup"><span data-stu-id="f0744-120">String</span></span>|  
|<span data-ttu-id="f0744-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-121">TABLE_TYPE</span></span>|<span data-ttu-id="f0744-122">String</span><span class="sxs-lookup"><span data-stu-id="f0744-122">String</span></span>|  
|<span data-ttu-id="f0744-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-123">TABLE_GUID</span></span>|<span data-ttu-id="f0744-124">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-124">Guid</span></span>|  
|<span data-ttu-id="f0744-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-125">DESCRIPTION</span></span>|<span data-ttu-id="f0744-126">String</span><span class="sxs-lookup"><span data-stu-id="f0744-126">String</span></span>|  
|<span data-ttu-id="f0744-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-127">TABLE_PROPID</span></span>|<span data-ttu-id="f0744-128">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-128">Int64</span></span>|  
|<span data-ttu-id="f0744-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f0744-129">DATE_CREATED</span></span>|<span data-ttu-id="f0744-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-130">DateTime</span></span>|  
|<span data-ttu-id="f0744-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f0744-131">DATE_MODIFIED</span></span>|<span data-ttu-id="f0744-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f0744-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="f0744-133">Columns</span></span>  
  
|<span data-ttu-id="f0744-134">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-134">ColumnName</span></span>|<span data-ttu-id="f0744-135">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-136">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-137">String</span><span class="sxs-lookup"><span data-stu-id="f0744-137">String</span></span>|  
|<span data-ttu-id="f0744-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-139">String</span><span class="sxs-lookup"><span data-stu-id="f0744-139">String</span></span>|  
|<span data-ttu-id="f0744-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-140">TABLE_NAME</span></span>|<span data-ttu-id="f0744-141">String</span><span class="sxs-lookup"><span data-stu-id="f0744-141">String</span></span>|  
|<span data-ttu-id="f0744-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-142">COLUMN_NAME</span></span>|<span data-ttu-id="f0744-143">String</span><span class="sxs-lookup"><span data-stu-id="f0744-143">String</span></span>|  
|<span data-ttu-id="f0744-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-144">COLUMN_GUID</span></span>|<span data-ttu-id="f0744-145">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-145">Guid</span></span>|  
|<span data-ttu-id="f0744-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-146">COLUMN_PROPID</span></span>|<span data-ttu-id="f0744-147">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-147">Int64</span></span>|  
|<span data-ttu-id="f0744-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f0744-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="f0744-149">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-149">Int64</span></span>|  
|<span data-ttu-id="f0744-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="f0744-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="f0744-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-151">Boolean</span></span>|  
|<span data-ttu-id="f0744-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="f0744-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="f0744-153">String</span><span class="sxs-lookup"><span data-stu-id="f0744-153">String</span></span>|  
|<span data-ttu-id="f0744-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="f0744-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="f0744-155">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-155">Int64</span></span>|  
|<span data-ttu-id="f0744-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f0744-156">IS_NULLABLE</span></span>|<span data-ttu-id="f0744-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-157">Boolean</span></span>|  
|<span data-ttu-id="f0744-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-158">DATA_TYPE</span></span>|<span data-ttu-id="f0744-159">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-159">Int32</span></span>|  
|<span data-ttu-id="f0744-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-160">TYPE_GUID</span></span>|<span data-ttu-id="f0744-161">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-161">Guid</span></span>|  
|<span data-ttu-id="f0744-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f0744-163">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-163">Int64</span></span>|  
|<span data-ttu-id="f0744-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f0744-165">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-165">Int64</span></span>|  
|<span data-ttu-id="f0744-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f0744-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f0744-167">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-167">Int32</span></span>|  
|<span data-ttu-id="f0744-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f0744-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="f0744-169">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-169">Int16</span></span>|  
|<span data-ttu-id="f0744-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f0744-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="f0744-171">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-171">Int64</span></span>|  
|<span data-ttu-id="f0744-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="f0744-173">String</span><span class="sxs-lookup"><span data-stu-id="f0744-173">String</span></span>|  
|<span data-ttu-id="f0744-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="f0744-175">String</span><span class="sxs-lookup"><span data-stu-id="f0744-175">String</span></span>|  
|<span data-ttu-id="f0744-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="f0744-177">String</span><span class="sxs-lookup"><span data-stu-id="f0744-177">String</span></span>|  
|<span data-ttu-id="f0744-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="f0744-179">String</span><span class="sxs-lookup"><span data-stu-id="f0744-179">String</span></span>|  
|<span data-ttu-id="f0744-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="f0744-181">String</span><span class="sxs-lookup"><span data-stu-id="f0744-181">String</span></span>|  
|<span data-ttu-id="f0744-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-182">COLLATION_NAME</span></span>|<span data-ttu-id="f0744-183">String</span><span class="sxs-lookup"><span data-stu-id="f0744-183">String</span></span>|  
|<span data-ttu-id="f0744-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="f0744-185">String</span><span class="sxs-lookup"><span data-stu-id="f0744-185">String</span></span>|  
|<span data-ttu-id="f0744-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="f0744-187">String</span><span class="sxs-lookup"><span data-stu-id="f0744-187">String</span></span>|  
|<span data-ttu-id="f0744-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-188">DOMAIN_NAME</span></span>|<span data-ttu-id="f0744-189">String</span><span class="sxs-lookup"><span data-stu-id="f0744-189">String</span></span>|  
|<span data-ttu-id="f0744-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-190">DESCRIPTION</span></span>|<span data-ttu-id="f0744-191">String</span><span class="sxs-lookup"><span data-stu-id="f0744-191">String</span></span>|  
|<span data-ttu-id="f0744-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="f0744-192">COLUMN_LCID</span></span>|<span data-ttu-id="f0744-193">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-193">Int32</span></span>|  
|<span data-ttu-id="f0744-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="f0744-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="f0744-195">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-195">Int32</span></span>|  
|<span data-ttu-id="f0744-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="f0744-196">COLUMN_SORTID</span></span>|<span data-ttu-id="f0744-197">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-197">Int32</span></span>|  
|<span data-ttu-id="f0744-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="f0744-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="f0744-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="f0744-199">Byte[]</span></span>|  
|<span data-ttu-id="f0744-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="f0744-200">IS_COMPUTED</span></span>|<span data-ttu-id="f0744-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f0744-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="f0744-202">Procedures</span></span>  
  
|<span data-ttu-id="f0744-203">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-203">ColumnName</span></span>|<span data-ttu-id="f0744-204">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f0744-206">String</span><span class="sxs-lookup"><span data-stu-id="f0744-206">String</span></span>|  
|<span data-ttu-id="f0744-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f0744-208">String</span><span class="sxs-lookup"><span data-stu-id="f0744-208">String</span></span>|  
|<span data-ttu-id="f0744-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="f0744-210">String</span><span class="sxs-lookup"><span data-stu-id="f0744-210">String</span></span>|  
|<span data-ttu-id="f0744-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f0744-212">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-212">Int16</span></span>|  
|<span data-ttu-id="f0744-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f0744-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="f0744-214">String</span><span class="sxs-lookup"><span data-stu-id="f0744-214">String</span></span>|  
|<span data-ttu-id="f0744-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-215">DESCRIPTION</span></span>|<span data-ttu-id="f0744-216">String</span><span class="sxs-lookup"><span data-stu-id="f0744-216">String</span></span>|  
|<span data-ttu-id="f0744-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f0744-217">DATE_CREATED</span></span>|<span data-ttu-id="f0744-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-218">DateTime</span></span>|  
|<span data-ttu-id="f0744-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f0744-219">DATE_MODIFIED</span></span>|<span data-ttu-id="f0744-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="f0744-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f0744-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="f0744-222">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-222">ColumnName</span></span>|<span data-ttu-id="f0744-223">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f0744-225">String</span><span class="sxs-lookup"><span data-stu-id="f0744-225">String</span></span>|  
|<span data-ttu-id="f0744-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f0744-227">String</span><span class="sxs-lookup"><span data-stu-id="f0744-227">String</span></span>|  
|<span data-ttu-id="f0744-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="f0744-229">String</span><span class="sxs-lookup"><span data-stu-id="f0744-229">String</span></span>|  
|<span data-ttu-id="f0744-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-230">PARAMETER_NAME</span></span>|<span data-ttu-id="f0744-231">String</span><span class="sxs-lookup"><span data-stu-id="f0744-231">String</span></span>|  
|<span data-ttu-id="f0744-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f0744-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="f0744-233">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-233">Int32</span></span>|  
|<span data-ttu-id="f0744-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="f0744-235">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-235">Int32</span></span>|  
|<span data-ttu-id="f0744-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="f0744-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="f0744-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-237">Boolean</span></span>|  
|<span data-ttu-id="f0744-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="f0744-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="f0744-239">String</span><span class="sxs-lookup"><span data-stu-id="f0744-239">String</span></span>|  
|<span data-ttu-id="f0744-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f0744-240">IS_NULLABLE</span></span>|<span data-ttu-id="f0744-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-241">Boolean</span></span>|  
|<span data-ttu-id="f0744-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-242">DATA_TYPE</span></span>|<span data-ttu-id="f0744-243">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-243">Int32</span></span>|  
|<span data-ttu-id="f0744-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f0744-245">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-245">Int64</span></span>|  
|<span data-ttu-id="f0744-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f0744-247">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-247">Int64</span></span>|  
|<span data-ttu-id="f0744-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f0744-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f0744-249">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-249">Int32</span></span>|  
|<span data-ttu-id="f0744-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f0744-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="f0744-251">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-251">Int16</span></span>|  
|<span data-ttu-id="f0744-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-252">DESCRIPTION</span></span>|<span data-ttu-id="f0744-253">String</span><span class="sxs-lookup"><span data-stu-id="f0744-253">String</span></span>|  
|<span data-ttu-id="f0744-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-254">TYPE_NAME</span></span>|<span data-ttu-id="f0744-255">String</span><span class="sxs-lookup"><span data-stu-id="f0744-255">String</span></span>|  
|<span data-ttu-id="f0744-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="f0744-257">String</span><span class="sxs-lookup"><span data-stu-id="f0744-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="f0744-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="f0744-258">Catalog</span></span>  
  
|<span data-ttu-id="f0744-259">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-259">ColumnName</span></span>|<span data-ttu-id="f0744-260">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-261">CATALOG_NAME</span></span>|<span data-ttu-id="f0744-262">String</span><span class="sxs-lookup"><span data-stu-id="f0744-262">String</span></span>|  
|<span data-ttu-id="f0744-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-263">DESCRIPTION</span></span>|<span data-ttu-id="f0744-264">String</span><span class="sxs-lookup"><span data-stu-id="f0744-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f0744-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="f0744-265">Indexes</span></span>  
  
|<span data-ttu-id="f0744-266">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-266">ColumnName</span></span>|<span data-ttu-id="f0744-267">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-268">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-269">String</span><span class="sxs-lookup"><span data-stu-id="f0744-269">String</span></span>|  
|<span data-ttu-id="f0744-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-271">String</span><span class="sxs-lookup"><span data-stu-id="f0744-271">String</span></span>|  
|<span data-ttu-id="f0744-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-272">TABLE_NAME</span></span>|<span data-ttu-id="f0744-273">String</span><span class="sxs-lookup"><span data-stu-id="f0744-273">String</span></span>|  
|<span data-ttu-id="f0744-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-274">INDEX_CATALOG</span></span>|<span data-ttu-id="f0744-275">String</span><span class="sxs-lookup"><span data-stu-id="f0744-275">String</span></span>|  
|<span data-ttu-id="f0744-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="f0744-277">String</span><span class="sxs-lookup"><span data-stu-id="f0744-277">String</span></span>|  
|<span data-ttu-id="f0744-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-278">INDEX_NAME</span></span>|<span data-ttu-id="f0744-279">String</span><span class="sxs-lookup"><span data-stu-id="f0744-279">String</span></span>|  
|<span data-ttu-id="f0744-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="f0744-280">PRIMARY_KEY</span></span>|<span data-ttu-id="f0744-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-281">Boolean</span></span>|  
|<span data-ttu-id="f0744-282">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="f0744-282">UNIQUE</span></span>|<span data-ttu-id="f0744-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-283">Boolean</span></span>|  
|<span data-ttu-id="f0744-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="f0744-284">CLUSTERED</span></span>|<span data-ttu-id="f0744-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-285">Boolean</span></span>|  
|<span data-ttu-id="f0744-286">TYP</span><span class="sxs-lookup"><span data-stu-id="f0744-286">TYPE</span></span>|<span data-ttu-id="f0744-287">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-287">Int32</span></span>|  
|<span data-ttu-id="f0744-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="f0744-288">FILL_FACTOR</span></span>|<span data-ttu-id="f0744-289">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-289">Int32</span></span>|  
|<span data-ttu-id="f0744-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="f0744-290">INITIAL_SIZE</span></span>|<span data-ttu-id="f0744-291">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-291">Int32</span></span>|  
|<span data-ttu-id="f0744-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="f0744-292">NULLS</span></span>|<span data-ttu-id="f0744-293">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-293">Int32</span></span>|  
|<span data-ttu-id="f0744-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="f0744-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="f0744-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-295">Boolean</span></span>|  
|<span data-ttu-id="f0744-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="f0744-296">AUTO_UPDATE</span></span>|<span data-ttu-id="f0744-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-297">Boolean</span></span>|  
|<span data-ttu-id="f0744-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="f0744-298">NULL_COLLATION</span></span>|<span data-ttu-id="f0744-299">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-299">Int32</span></span>|  
|<span data-ttu-id="f0744-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f0744-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="f0744-301">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-301">Int64</span></span>|  
|<span data-ttu-id="f0744-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-302">COLUMN_NAME</span></span>|<span data-ttu-id="f0744-303">String</span><span class="sxs-lookup"><span data-stu-id="f0744-303">String</span></span>|  
|<span data-ttu-id="f0744-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-304">COLUMN_GUID</span></span>|<span data-ttu-id="f0744-305">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-305">Guid</span></span>|  
|<span data-ttu-id="f0744-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-306">COLUMN_PROPID</span></span>|<span data-ttu-id="f0744-307">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-307">Int64</span></span>|  
|<span data-ttu-id="f0744-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="f0744-308">COLLATION</span></span>|<span data-ttu-id="f0744-309">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-309">Int16</span></span>|  
|<span data-ttu-id="f0744-310">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="f0744-310">CARDINALITY</span></span>|<span data-ttu-id="f0744-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="f0744-311">Decimal</span></span>|  
|<span data-ttu-id="f0744-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="f0744-312">PAGES</span></span>|<span data-ttu-id="f0744-313">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-313">Int32</span></span>|  
|<span data-ttu-id="f0744-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f0744-314">FILTER_CONDITION</span></span>|<span data-ttu-id="f0744-315">String</span><span class="sxs-lookup"><span data-stu-id="f0744-315">String</span></span>|  
|<span data-ttu-id="f0744-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="f0744-316">INTEGRATED</span></span>|<span data-ttu-id="f0744-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="f0744-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="f0744-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="f0744-319">Oracle OLE DB ovladače Microsoft podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="f0744-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f0744-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="f0744-320">Tables</span></span>  
  
-   <span data-ttu-id="f0744-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="f0744-321">Columns</span></span>  
  
-   <span data-ttu-id="f0744-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="f0744-322">Procedures</span></span>  
  
-   <span data-ttu-id="f0744-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f0744-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="f0744-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f0744-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="f0744-325">zobrazení</span><span class="sxs-lookup"><span data-stu-id="f0744-325">Views</span></span>  
  
-   <span data-ttu-id="f0744-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="f0744-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="f0744-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="f0744-327">Tables</span></span>  
  
|<span data-ttu-id="f0744-328">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-328">ColumnName</span></span>|<span data-ttu-id="f0744-329">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-330">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-331">String</span><span class="sxs-lookup"><span data-stu-id="f0744-331">String</span></span>|  
|<span data-ttu-id="f0744-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-333">String</span><span class="sxs-lookup"><span data-stu-id="f0744-333">String</span></span>|  
|<span data-ttu-id="f0744-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-334">TABLE_NAME</span></span>|<span data-ttu-id="f0744-335">String</span><span class="sxs-lookup"><span data-stu-id="f0744-335">String</span></span>|  
|<span data-ttu-id="f0744-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-336">TABLE_TYPE</span></span>|<span data-ttu-id="f0744-337">String</span><span class="sxs-lookup"><span data-stu-id="f0744-337">String</span></span>|  
|<span data-ttu-id="f0744-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-338">TABLE_GUID</span></span>|<span data-ttu-id="f0744-339">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-339">Guid</span></span>|  
|<span data-ttu-id="f0744-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-340">DESCRIPTION</span></span>|<span data-ttu-id="f0744-341">String</span><span class="sxs-lookup"><span data-stu-id="f0744-341">String</span></span>|  
|<span data-ttu-id="f0744-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-342">TABLE_PROPID</span></span>|<span data-ttu-id="f0744-343">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-343">Int64</span></span>|  
|<span data-ttu-id="f0744-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f0744-344">DATE_CREATED</span></span>|<span data-ttu-id="f0744-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-345">DateTime</span></span>|  
|<span data-ttu-id="f0744-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f0744-346">DATE_MODIFIED</span></span>|<span data-ttu-id="f0744-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f0744-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="f0744-348">Columns</span></span>  
  
|<span data-ttu-id="f0744-349">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-349">ColumnName</span></span>|<span data-ttu-id="f0744-350">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-351">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-352">String</span><span class="sxs-lookup"><span data-stu-id="f0744-352">String</span></span>|  
|<span data-ttu-id="f0744-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-354">String</span><span class="sxs-lookup"><span data-stu-id="f0744-354">String</span></span>|  
|<span data-ttu-id="f0744-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-355">TABLE_NAME</span></span>|<span data-ttu-id="f0744-356">String</span><span class="sxs-lookup"><span data-stu-id="f0744-356">String</span></span>|  
|<span data-ttu-id="f0744-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-357">COLUMN_NAME</span></span>|<span data-ttu-id="f0744-358">String</span><span class="sxs-lookup"><span data-stu-id="f0744-358">String</span></span>|  
|<span data-ttu-id="f0744-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-359">COLUMN_GUID</span></span>|<span data-ttu-id="f0744-360">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-360">Guid</span></span>|  
|<span data-ttu-id="f0744-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-361">COLUMN_PROPID</span></span>|<span data-ttu-id="f0744-362">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-362">Int64</span></span>|  
|<span data-ttu-id="f0744-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f0744-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="f0744-364">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-364">Int64</span></span>|  
|<span data-ttu-id="f0744-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="f0744-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="f0744-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-366">Boolean</span></span>|  
|<span data-ttu-id="f0744-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="f0744-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="f0744-368">String</span><span class="sxs-lookup"><span data-stu-id="f0744-368">String</span></span>|  
|<span data-ttu-id="f0744-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="f0744-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="f0744-370">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-370">Int64</span></span>|  
|<span data-ttu-id="f0744-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f0744-371">IS_NULLABLE</span></span>|<span data-ttu-id="f0744-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-372">Boolean</span></span>|  
|<span data-ttu-id="f0744-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-373">DATA_TYPE</span></span>|<span data-ttu-id="f0744-374">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-374">Int32</span></span>|  
|<span data-ttu-id="f0744-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-375">TYPE_GUID</span></span>|<span data-ttu-id="f0744-376">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-376">Guid</span></span>|  
|<span data-ttu-id="f0744-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f0744-378">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-378">Int64</span></span>|  
|<span data-ttu-id="f0744-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f0744-380">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-380">Int64</span></span>|  
|<span data-ttu-id="f0744-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f0744-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f0744-382">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-382">Int32</span></span>|  
|<span data-ttu-id="f0744-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f0744-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="f0744-384">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-384">Int16</span></span>|  
|<span data-ttu-id="f0744-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f0744-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="f0744-386">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-386">Int64</span></span>|  
|<span data-ttu-id="f0744-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="f0744-388">String</span><span class="sxs-lookup"><span data-stu-id="f0744-388">String</span></span>|  
|<span data-ttu-id="f0744-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="f0744-390">String</span><span class="sxs-lookup"><span data-stu-id="f0744-390">String</span></span>|  
|<span data-ttu-id="f0744-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="f0744-392">String</span><span class="sxs-lookup"><span data-stu-id="f0744-392">String</span></span>|  
|<span data-ttu-id="f0744-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="f0744-394">String</span><span class="sxs-lookup"><span data-stu-id="f0744-394">String</span></span>|  
|<span data-ttu-id="f0744-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="f0744-396">String</span><span class="sxs-lookup"><span data-stu-id="f0744-396">String</span></span>|  
|<span data-ttu-id="f0744-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-397">COLLATION_NAME</span></span>|<span data-ttu-id="f0744-398">String</span><span class="sxs-lookup"><span data-stu-id="f0744-398">String</span></span>|  
|<span data-ttu-id="f0744-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="f0744-400">String</span><span class="sxs-lookup"><span data-stu-id="f0744-400">String</span></span>|  
|<span data-ttu-id="f0744-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="f0744-402">String</span><span class="sxs-lookup"><span data-stu-id="f0744-402">String</span></span>|  
|<span data-ttu-id="f0744-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-403">DOMAIN_NAME</span></span>|<span data-ttu-id="f0744-404">String</span><span class="sxs-lookup"><span data-stu-id="f0744-404">String</span></span>|  
|<span data-ttu-id="f0744-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-405">DESCRIPTION</span></span>|<span data-ttu-id="f0744-406">String</span><span class="sxs-lookup"><span data-stu-id="f0744-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f0744-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="f0744-407">Procedures</span></span>  
  
|<span data-ttu-id="f0744-408">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-408">ColumnName</span></span>|<span data-ttu-id="f0744-409">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f0744-411">String</span><span class="sxs-lookup"><span data-stu-id="f0744-411">String</span></span>|  
|<span data-ttu-id="f0744-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f0744-413">String</span><span class="sxs-lookup"><span data-stu-id="f0744-413">String</span></span>|  
|<span data-ttu-id="f0744-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="f0744-415">String</span><span class="sxs-lookup"><span data-stu-id="f0744-415">String</span></span>|  
|<span data-ttu-id="f0744-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f0744-417">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-417">Int16</span></span>|  
|<span data-ttu-id="f0744-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f0744-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="f0744-419">String</span><span class="sxs-lookup"><span data-stu-id="f0744-419">String</span></span>|  
|<span data-ttu-id="f0744-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-420">DESCRIPTION</span></span>|<span data-ttu-id="f0744-421">String</span><span class="sxs-lookup"><span data-stu-id="f0744-421">String</span></span>|  
|<span data-ttu-id="f0744-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f0744-422">DATE_CREATED</span></span>|<span data-ttu-id="f0744-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-423">DateTime</span></span>|  
|<span data-ttu-id="f0744-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f0744-424">DATE_MODIFIED</span></span>|<span data-ttu-id="f0744-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="f0744-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f0744-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="f0744-427">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-427">ColumnName</span></span>|<span data-ttu-id="f0744-428">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f0744-430">String</span><span class="sxs-lookup"><span data-stu-id="f0744-430">String</span></span>|  
|<span data-ttu-id="f0744-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f0744-432">String</span><span class="sxs-lookup"><span data-stu-id="f0744-432">String</span></span>|  
|<span data-ttu-id="f0744-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="f0744-434">String</span><span class="sxs-lookup"><span data-stu-id="f0744-434">String</span></span>|  
|<span data-ttu-id="f0744-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-435">COLUMN_NAME</span></span>|<span data-ttu-id="f0744-436">String</span><span class="sxs-lookup"><span data-stu-id="f0744-436">String</span></span>|  
|<span data-ttu-id="f0744-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-437">COLUMN_GUID</span></span>|<span data-ttu-id="f0744-438">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-438">Guid</span></span>|  
|<span data-ttu-id="f0744-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-439">COLUMN_PROPID</span></span>|<span data-ttu-id="f0744-440">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-440">Int64</span></span>|  
|<span data-ttu-id="f0744-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="f0744-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="f0744-442">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-442">Int64</span></span>|  
|<span data-ttu-id="f0744-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f0744-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="f0744-444">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-444">Int64</span></span>|  
|<span data-ttu-id="f0744-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f0744-445">IS_NULLABLE</span></span>|<span data-ttu-id="f0744-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-446">Boolean</span></span>|  
|<span data-ttu-id="f0744-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-447">DATA_TYPE</span></span>|<span data-ttu-id="f0744-448">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-448">Int32</span></span>|  
|<span data-ttu-id="f0744-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-449">TYPE_GUID</span></span>|<span data-ttu-id="f0744-450">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-450">Guid</span></span>|  
|<span data-ttu-id="f0744-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f0744-452">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-452">Int64</span></span>|  
|<span data-ttu-id="f0744-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f0744-454">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-454">Int64</span></span>|  
|<span data-ttu-id="f0744-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f0744-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f0744-456">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-456">Int32</span></span>|  
|<span data-ttu-id="f0744-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f0744-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="f0744-458">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-458">Int16</span></span>|  
|<span data-ttu-id="f0744-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-459">DESCRIPTION</span></span>|<span data-ttu-id="f0744-460">String</span><span class="sxs-lookup"><span data-stu-id="f0744-460">String</span></span>|  
|<span data-ttu-id="f0744-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="f0744-461">OVERLOAD</span></span>|<span data-ttu-id="f0744-462">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="f0744-463">zobrazení</span><span class="sxs-lookup"><span data-stu-id="f0744-463">Views</span></span>  
  
|<span data-ttu-id="f0744-464">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-464">ColumnName</span></span>|<span data-ttu-id="f0744-465">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-466">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-467">String</span><span class="sxs-lookup"><span data-stu-id="f0744-467">String</span></span>|  
|<span data-ttu-id="f0744-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-469">String</span><span class="sxs-lookup"><span data-stu-id="f0744-469">String</span></span>|  
|<span data-ttu-id="f0744-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-470">TABLE_NAME</span></span>|<span data-ttu-id="f0744-471">String</span><span class="sxs-lookup"><span data-stu-id="f0744-471">String</span></span>|  
|<span data-ttu-id="f0744-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f0744-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="f0744-473">String</span><span class="sxs-lookup"><span data-stu-id="f0744-473">String</span></span>|  
|<span data-ttu-id="f0744-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="f0744-474">CHECK_OPTION</span></span>|<span data-ttu-id="f0744-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-475">Boolean</span></span>|  
|<span data-ttu-id="f0744-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="f0744-476">IS_UPDATABLE</span></span>|<span data-ttu-id="f0744-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-477">Boolean</span></span>|  
|<span data-ttu-id="f0744-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-478">DESCRIPTION</span></span>|<span data-ttu-id="f0744-479">String</span><span class="sxs-lookup"><span data-stu-id="f0744-479">String</span></span>|  
|<span data-ttu-id="f0744-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f0744-480">DATE_CREATED</span></span>|<span data-ttu-id="f0744-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-481">DateTime</span></span>|  
|<span data-ttu-id="f0744-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f0744-482">DATE_MODIFIED</span></span>|<span data-ttu-id="f0744-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f0744-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="f0744-484">Indexes</span></span>  
  
|<span data-ttu-id="f0744-485">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-485">ColumnName</span></span>|<span data-ttu-id="f0744-486">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-487">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-488">String</span><span class="sxs-lookup"><span data-stu-id="f0744-488">String</span></span>|  
|<span data-ttu-id="f0744-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-490">String</span><span class="sxs-lookup"><span data-stu-id="f0744-490">String</span></span>|  
|<span data-ttu-id="f0744-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-491">TABLE_NAME</span></span>|<span data-ttu-id="f0744-492">String</span><span class="sxs-lookup"><span data-stu-id="f0744-492">String</span></span>|  
|<span data-ttu-id="f0744-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-493">INDEX_CATALOG</span></span>|<span data-ttu-id="f0744-494">String</span><span class="sxs-lookup"><span data-stu-id="f0744-494">String</span></span>|  
|<span data-ttu-id="f0744-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="f0744-496">String</span><span class="sxs-lookup"><span data-stu-id="f0744-496">String</span></span>|  
|<span data-ttu-id="f0744-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-497">INDEX_NAME</span></span>|<span data-ttu-id="f0744-498">String</span><span class="sxs-lookup"><span data-stu-id="f0744-498">String</span></span>|  
|<span data-ttu-id="f0744-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="f0744-499">PRIMARY_KEY</span></span>|<span data-ttu-id="f0744-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-500">Boolean</span></span>|  
|<span data-ttu-id="f0744-501">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="f0744-501">UNIQUE</span></span>|<span data-ttu-id="f0744-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-502">Boolean</span></span>|  
|<span data-ttu-id="f0744-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="f0744-503">CLUSTERED</span></span>|<span data-ttu-id="f0744-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-504">Boolean</span></span>|  
|<span data-ttu-id="f0744-505">TYP</span><span class="sxs-lookup"><span data-stu-id="f0744-505">TYPE</span></span>|<span data-ttu-id="f0744-506">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-506">Int32</span></span>|  
|<span data-ttu-id="f0744-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="f0744-507">FILL_FACTOR</span></span>|<span data-ttu-id="f0744-508">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-508">Int32</span></span>|  
|<span data-ttu-id="f0744-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="f0744-509">INITIAL_SIZE</span></span>|<span data-ttu-id="f0744-510">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-510">Int32</span></span>|  
|<span data-ttu-id="f0744-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="f0744-511">NULLS</span></span>|<span data-ttu-id="f0744-512">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-512">Int32</span></span>|  
|<span data-ttu-id="f0744-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="f0744-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="f0744-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-514">Boolean</span></span>|  
|<span data-ttu-id="f0744-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="f0744-515">AUTO_UPDATE</span></span>|<span data-ttu-id="f0744-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-516">Boolean</span></span>|  
|<span data-ttu-id="f0744-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="f0744-517">NULL_COLLATION</span></span>|<span data-ttu-id="f0744-518">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-518">Int32</span></span>|  
|<span data-ttu-id="f0744-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f0744-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="f0744-520">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-520">Int64</span></span>|  
|<span data-ttu-id="f0744-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-521">COLUMN_NAME</span></span>|<span data-ttu-id="f0744-522">String</span><span class="sxs-lookup"><span data-stu-id="f0744-522">String</span></span>|  
|<span data-ttu-id="f0744-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-523">COLUMN_GUID</span></span>|<span data-ttu-id="f0744-524">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-524">Guid</span></span>|  
|<span data-ttu-id="f0744-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-525">COLUMN_PROPID</span></span>|<span data-ttu-id="f0744-526">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-526">Int64</span></span>|  
|<span data-ttu-id="f0744-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="f0744-527">COLLATION</span></span>|<span data-ttu-id="f0744-528">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-528">Int16</span></span>|  
|<span data-ttu-id="f0744-529">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="f0744-529">CARDINALITY</span></span>|<span data-ttu-id="f0744-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="f0744-530">Decimal</span></span>|  
|<span data-ttu-id="f0744-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="f0744-531">PAGES</span></span>|<span data-ttu-id="f0744-532">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-532">Int32</span></span>|  
|<span data-ttu-id="f0744-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f0744-533">FILTER_CONDITION</span></span>|<span data-ttu-id="f0744-534">String</span><span class="sxs-lookup"><span data-stu-id="f0744-534">String</span></span>|  
|<span data-ttu-id="f0744-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="f0744-535">INTEGRATED</span></span>|<span data-ttu-id="f0744-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="f0744-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="f0744-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="f0744-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="f0744-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="f0744-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="f0744-539">Tables</span></span>  
  
-   <span data-ttu-id="f0744-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="f0744-540">Columns</span></span>  
  
-   <span data-ttu-id="f0744-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="f0744-541">Procedures</span></span>  
  
-   <span data-ttu-id="f0744-542">zobrazení</span><span class="sxs-lookup"><span data-stu-id="f0744-542">Views</span></span>  
  
-   <span data-ttu-id="f0744-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="f0744-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="f0744-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="f0744-544">Tables</span></span>  
  
|<span data-ttu-id="f0744-545">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-545">ColumnName</span></span>|<span data-ttu-id="f0744-546">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-547">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-548">String</span><span class="sxs-lookup"><span data-stu-id="f0744-548">String</span></span>|  
|<span data-ttu-id="f0744-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-550">String</span><span class="sxs-lookup"><span data-stu-id="f0744-550">String</span></span>|  
|<span data-ttu-id="f0744-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-551">TABLE_NAME</span></span>|<span data-ttu-id="f0744-552">String</span><span class="sxs-lookup"><span data-stu-id="f0744-552">String</span></span>|  
|<span data-ttu-id="f0744-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-553">TABLE_TYPE</span></span>|<span data-ttu-id="f0744-554">String</span><span class="sxs-lookup"><span data-stu-id="f0744-554">String</span></span>|  
|<span data-ttu-id="f0744-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-555">TABLE_GUID</span></span>|<span data-ttu-id="f0744-556">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-556">Guid</span></span>|  
|<span data-ttu-id="f0744-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-557">DESCRIPTION</span></span>|<span data-ttu-id="f0744-558">String</span><span class="sxs-lookup"><span data-stu-id="f0744-558">String</span></span>|  
|<span data-ttu-id="f0744-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-559">TABLE_PROPID</span></span>|<span data-ttu-id="f0744-560">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-560">Int64</span></span>|  
|<span data-ttu-id="f0744-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f0744-561">DATE_CREATED</span></span>|<span data-ttu-id="f0744-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-562">DateTime</span></span>|  
|<span data-ttu-id="f0744-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f0744-563">DATE_MODIFIED</span></span>|<span data-ttu-id="f0744-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="f0744-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="f0744-565">Columns</span></span>  
  
|<span data-ttu-id="f0744-566">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-566">ColumnName</span></span>|<span data-ttu-id="f0744-567">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-568">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-569">String</span><span class="sxs-lookup"><span data-stu-id="f0744-569">String</span></span>|  
|<span data-ttu-id="f0744-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-571">String</span><span class="sxs-lookup"><span data-stu-id="f0744-571">String</span></span>|  
|<span data-ttu-id="f0744-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-572">TABLE_NAME</span></span>|<span data-ttu-id="f0744-573">String</span><span class="sxs-lookup"><span data-stu-id="f0744-573">String</span></span>|  
|<span data-ttu-id="f0744-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-574">COLUMN_NAME</span></span>|<span data-ttu-id="f0744-575">String</span><span class="sxs-lookup"><span data-stu-id="f0744-575">String</span></span>|  
|<span data-ttu-id="f0744-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-576">COLUMN_GUID</span></span>|<span data-ttu-id="f0744-577">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-577">Guid</span></span>|  
|<span data-ttu-id="f0744-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-578">COLUMN_PROPID</span></span>|<span data-ttu-id="f0744-579">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-579">Int64</span></span>|  
|<span data-ttu-id="f0744-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f0744-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="f0744-581">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-581">Int64</span></span>|  
|<span data-ttu-id="f0744-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="f0744-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="f0744-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-583">Boolean</span></span>|  
|<span data-ttu-id="f0744-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="f0744-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="f0744-585">String</span><span class="sxs-lookup"><span data-stu-id="f0744-585">String</span></span>|  
|<span data-ttu-id="f0744-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="f0744-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="f0744-587">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-587">Int64</span></span>|  
|<span data-ttu-id="f0744-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f0744-588">IS_NULLABLE</span></span>|<span data-ttu-id="f0744-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-589">Boolean</span></span>|  
|<span data-ttu-id="f0744-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-590">DATA_TYPE</span></span>|<span data-ttu-id="f0744-591">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-591">Int32</span></span>|  
|<span data-ttu-id="f0744-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-592">TYPE_GUID</span></span>|<span data-ttu-id="f0744-593">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-593">Guid</span></span>|  
|<span data-ttu-id="f0744-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="f0744-595">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-595">Int64</span></span>|  
|<span data-ttu-id="f0744-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f0744-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="f0744-597">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-597">Int64</span></span>|  
|<span data-ttu-id="f0744-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f0744-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="f0744-599">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-599">Int32</span></span>|  
|<span data-ttu-id="f0744-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="f0744-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="f0744-601">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-601">Int16</span></span>|  
|<span data-ttu-id="f0744-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="f0744-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="f0744-603">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-603">Int64</span></span>|  
|<span data-ttu-id="f0744-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="f0744-605">String</span><span class="sxs-lookup"><span data-stu-id="f0744-605">String</span></span>|  
|<span data-ttu-id="f0744-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="f0744-607">String</span><span class="sxs-lookup"><span data-stu-id="f0744-607">String</span></span>|  
|<span data-ttu-id="f0744-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="f0744-609">String</span><span class="sxs-lookup"><span data-stu-id="f0744-609">String</span></span>|  
|<span data-ttu-id="f0744-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="f0744-611">String</span><span class="sxs-lookup"><span data-stu-id="f0744-611">String</span></span>|  
|<span data-ttu-id="f0744-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="f0744-613">String</span><span class="sxs-lookup"><span data-stu-id="f0744-613">String</span></span>|  
|<span data-ttu-id="f0744-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-614">COLLATION_NAME</span></span>|<span data-ttu-id="f0744-615">String</span><span class="sxs-lookup"><span data-stu-id="f0744-615">String</span></span>|  
|<span data-ttu-id="f0744-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="f0744-617">String</span><span class="sxs-lookup"><span data-stu-id="f0744-617">String</span></span>|  
|<span data-ttu-id="f0744-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="f0744-619">String</span><span class="sxs-lookup"><span data-stu-id="f0744-619">String</span></span>|  
|<span data-ttu-id="f0744-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-620">DOMAIN_NAME</span></span>|<span data-ttu-id="f0744-621">String</span><span class="sxs-lookup"><span data-stu-id="f0744-621">String</span></span>|  
|<span data-ttu-id="f0744-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-622">DESCRIPTION</span></span>|<span data-ttu-id="f0744-623">String</span><span class="sxs-lookup"><span data-stu-id="f0744-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="f0744-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="f0744-624">Procedures</span></span>  
  
|<span data-ttu-id="f0744-625">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-625">ColumnName</span></span>|<span data-ttu-id="f0744-626">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="f0744-628">String</span><span class="sxs-lookup"><span data-stu-id="f0744-628">String</span></span>|  
|<span data-ttu-id="f0744-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="f0744-630">String</span><span class="sxs-lookup"><span data-stu-id="f0744-630">String</span></span>|  
|<span data-ttu-id="f0744-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="f0744-632">String</span><span class="sxs-lookup"><span data-stu-id="f0744-632">String</span></span>|  
|<span data-ttu-id="f0744-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f0744-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f0744-634">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-634">Int16</span></span>|  
|<span data-ttu-id="f0744-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f0744-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="f0744-636">String</span><span class="sxs-lookup"><span data-stu-id="f0744-636">String</span></span>|  
|<span data-ttu-id="f0744-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-637">DESCRIPTION</span></span>|<span data-ttu-id="f0744-638">String</span><span class="sxs-lookup"><span data-stu-id="f0744-638">String</span></span>|  
|<span data-ttu-id="f0744-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f0744-639">DATE_CREATED</span></span>|<span data-ttu-id="f0744-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-640">DateTime</span></span>|  
|<span data-ttu-id="f0744-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f0744-641">DATE_MODIFIED</span></span>|<span data-ttu-id="f0744-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="f0744-643">zobrazení</span><span class="sxs-lookup"><span data-stu-id="f0744-643">Views</span></span>  
  
|<span data-ttu-id="f0744-644">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-644">ColumnName</span></span>|<span data-ttu-id="f0744-645">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-646">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-647">String</span><span class="sxs-lookup"><span data-stu-id="f0744-647">String</span></span>|  
|<span data-ttu-id="f0744-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-649">String</span><span class="sxs-lookup"><span data-stu-id="f0744-649">String</span></span>|  
|<span data-ttu-id="f0744-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-650">TABLE_NAME</span></span>|<span data-ttu-id="f0744-651">String</span><span class="sxs-lookup"><span data-stu-id="f0744-651">String</span></span>|  
|<span data-ttu-id="f0744-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="f0744-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="f0744-653">String</span><span class="sxs-lookup"><span data-stu-id="f0744-653">String</span></span>|  
|<span data-ttu-id="f0744-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="f0744-654">CHECK_OPTION</span></span>|<span data-ttu-id="f0744-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-655">Boolean</span></span>|  
|<span data-ttu-id="f0744-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="f0744-656">IS_UPDATABLE</span></span>|<span data-ttu-id="f0744-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-657">Boolean</span></span>|  
|<span data-ttu-id="f0744-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="f0744-658">DESCRIPTION</span></span>|<span data-ttu-id="f0744-659">String</span><span class="sxs-lookup"><span data-stu-id="f0744-659">String</span></span>|  
|<span data-ttu-id="f0744-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f0744-660">DATE_CREATED</span></span>|<span data-ttu-id="f0744-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-661">DateTime</span></span>|  
|<span data-ttu-id="f0744-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="f0744-662">DATE_MODIFIED</span></span>|<span data-ttu-id="f0744-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="f0744-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="f0744-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="f0744-664">Indexes</span></span>  
  
|<span data-ttu-id="f0744-665">columnName</span><span class="sxs-lookup"><span data-stu-id="f0744-665">ColumnName</span></span>|<span data-ttu-id="f0744-666">Datový typ</span><span class="sxs-lookup"><span data-stu-id="f0744-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="f0744-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-667">TABLE_CATALOG</span></span>|<span data-ttu-id="f0744-668">String</span><span class="sxs-lookup"><span data-stu-id="f0744-668">String</span></span>|  
|<span data-ttu-id="f0744-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="f0744-670">String</span><span class="sxs-lookup"><span data-stu-id="f0744-670">String</span></span>|  
|<span data-ttu-id="f0744-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-671">TABLE_NAME</span></span>|<span data-ttu-id="f0744-672">String</span><span class="sxs-lookup"><span data-stu-id="f0744-672">String</span></span>|  
|<span data-ttu-id="f0744-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f0744-673">INDEX_CATALOG</span></span>|<span data-ttu-id="f0744-674">String</span><span class="sxs-lookup"><span data-stu-id="f0744-674">String</span></span>|  
|<span data-ttu-id="f0744-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f0744-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="f0744-676">String</span><span class="sxs-lookup"><span data-stu-id="f0744-676">String</span></span>|  
|<span data-ttu-id="f0744-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-677">INDEX_NAME</span></span>|<span data-ttu-id="f0744-678">String</span><span class="sxs-lookup"><span data-stu-id="f0744-678">String</span></span>|  
|<span data-ttu-id="f0744-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="f0744-679">PRIMARY_KEY</span></span>|<span data-ttu-id="f0744-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-680">Boolean</span></span>|  
|<span data-ttu-id="f0744-681">JEDINEČNÉ</span><span class="sxs-lookup"><span data-stu-id="f0744-681">UNIQUE</span></span>|<span data-ttu-id="f0744-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-682">Boolean</span></span>|  
|<span data-ttu-id="f0744-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="f0744-683">CLUSTERED</span></span>|<span data-ttu-id="f0744-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-684">Boolean</span></span>|  
|<span data-ttu-id="f0744-685">TYP</span><span class="sxs-lookup"><span data-stu-id="f0744-685">TYPE</span></span>|<span data-ttu-id="f0744-686">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-686">Int32</span></span>|  
|<span data-ttu-id="f0744-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="f0744-687">FILL_FACTOR</span></span>|<span data-ttu-id="f0744-688">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-688">Int32</span></span>|  
|<span data-ttu-id="f0744-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="f0744-689">INITIAL_SIZE</span></span>|<span data-ttu-id="f0744-690">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-690">Int32</span></span>|  
|<span data-ttu-id="f0744-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="f0744-691">NULLS</span></span>|<span data-ttu-id="f0744-692">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-692">Int32</span></span>|  
|<span data-ttu-id="f0744-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="f0744-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="f0744-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-694">Boolean</span></span>|  
|<span data-ttu-id="f0744-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="f0744-695">AUTO_UPDATE</span></span>|<span data-ttu-id="f0744-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-696">Boolean</span></span>|  
|<span data-ttu-id="f0744-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="f0744-697">NULL_COLLATION</span></span>|<span data-ttu-id="f0744-698">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-698">Int32</span></span>|  
|<span data-ttu-id="f0744-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f0744-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="f0744-700">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-700">Int64</span></span>|  
|<span data-ttu-id="f0744-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f0744-701">COLUMN_NAME</span></span>|<span data-ttu-id="f0744-702">String</span><span class="sxs-lookup"><span data-stu-id="f0744-702">String</span></span>|  
|<span data-ttu-id="f0744-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-703">COLUMN_GUID</span></span>|<span data-ttu-id="f0744-704">Identifikátor GUID</span><span class="sxs-lookup"><span data-stu-id="f0744-704">Guid</span></span>|  
|<span data-ttu-id="f0744-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="f0744-705">COLUMN_PROPID</span></span>|<span data-ttu-id="f0744-706">Int64</span><span class="sxs-lookup"><span data-stu-id="f0744-706">Int64</span></span>|  
|<span data-ttu-id="f0744-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="f0744-707">COLLATION</span></span>|<span data-ttu-id="f0744-708">Int16</span><span class="sxs-lookup"><span data-stu-id="f0744-708">Int16</span></span>|  
|<span data-ttu-id="f0744-709">MOHUTNOST</span><span class="sxs-lookup"><span data-stu-id="f0744-709">CARDINALITY</span></span>|<span data-ttu-id="f0744-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="f0744-710">Decimal</span></span>|  
|<span data-ttu-id="f0744-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="f0744-711">PAGES</span></span>|<span data-ttu-id="f0744-712">Int32</span><span class="sxs-lookup"><span data-stu-id="f0744-712">Int32</span></span>|  
|<span data-ttu-id="f0744-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f0744-713">FILTER_CONDITION</span></span>|<span data-ttu-id="f0744-714">String</span><span class="sxs-lookup"><span data-stu-id="f0744-714">String</span></span>|  
|<span data-ttu-id="f0744-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="f0744-715">INTEGRATED</span></span>|<span data-ttu-id="f0744-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="f0744-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0744-717">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0744-717">See Also</span></span>  
 [<span data-ttu-id="f0744-718">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="f0744-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
