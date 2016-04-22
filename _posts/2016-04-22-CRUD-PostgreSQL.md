---
layout: post
title:  CRUD PostgreSQL
date:   2016-04-22
categories: programming
---

I've been working my way around postgresql lately. I am getting tired of Googling for every CRUD command in postgres. 

I don't have the muscle memory for these SQL commands specially done the Postgres way. Just to make it faster, I'm putting them here for easy access.

# CRUD

These are very basic commands to run in Postgres. The SQL keywords can be small letters. I am not sure if that applies to the table names as well.

## Read

Shows all the fields and rows in the Incident table.

	SELECT * FROM public."Incident";

Shows rows that satisfies the condition.
	
	SELECT * FROM public."Field" WHERE field_id = 143;

God knows why do I have to prefix the table name with `public.`  

## Create

This will create a row in the Field table.

	INSERT INTO public."Field" VALUES (210, 'IS', 'Summary of Events', 'Summary of Events', '' , 'T');

## Update 

This will look for the row with the specific field_id, then updates the type.

	UPDATE public."Field" SET type='IS' WHERE field_id = 143;

## Delete

Deletes a row if it matches the criteria.

	DELETE FROM public."Field" WHERE "Field".field_id = 210;

> I'm really getting involved in databases nowadays. It's nice to keep this handy. 